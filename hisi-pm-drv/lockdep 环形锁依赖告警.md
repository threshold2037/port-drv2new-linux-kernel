# 一次 Linux 5.15 内核移植中的 cpufreq 驱动排障实录

 > 
 > 关键词：lockdep、possible circular locking dependency、cpu_hotplug_lock、cpufreq、驱动移植、ABBA 死锁、LTP
 > 环境：Hi3798MX 平台（ARM32）/ 内核 5.15.134_s40 / 驱动模块 hi_pmoc / governor: userspace

## 背景介绍

项目背景：手上的 SDK 是 `HiSTBLinuxV100R005C00SPC041B020`，内核基线是 **linux-3.18**，硬件平台 hi3798mv100。把这套 SDK 里的驱动整体移植到 **linux-5.15** 上。3.18 → 5.15 中间跨了七年、十几个大版本，内核内部的锁模型、API 语义、结构体成员都发生了大量变化，而厂商驱动（尤其是电源管理、cpufreq 这类与 CPU 核心机制紧耦合的模块）恰恰是这些变化的重灾区。

本文的主要涉及的是 `hi_pmoc` 模块里的 cpufreq 驱动，核心函数 `hi_cpufreq_target()`（驱动的 `->target()` 回调）和 `hi_cpufreq_scale()`。

**验证手段**也很典型：内核打开了 `CONFIG_PROVE_LOCKING`（lockdep 的完整校验），用 **LTP（Linux Test Project）** 跑 CPU 热插拔用例。正是这两个组合拳，把一个"深埋在代码里"的锁序问题给暴露出来。

这类问题的价值在于：它不是一个"改个 API 名字就能编译过"的编译期错误，而是一个编译通过、功能正常、只有在特定并发时序下才会引爆的隐患。所以即便你已经把驱动跑起来了，也值得按下面的思路把它翻出来看一遍。

## 一、问题描述

**现象**：用 LTP 跑 CPU 热插拔测试时出现 hung 死。打开CONFIG_PROVE_LOCKING，内核启动日志出现下面这段 lockdep 告警（关键片段）：

````
======================================================
WARNING: possible circular locking dependency detected
5.15.134_s40 #432 Not tainted
------------------------------------------------------
kworker/3:0/28 is trying to acquire lock:
8102a8a4 (cpu_hotplug_lock){++++}-{0:0}, at: hi_cpufreq_target+0x30c/0x474 [hi_pmoc]

but task is already holding lock:
7f7834e0 (hi_cpufreq_lock){+.+.}-{3:3}, at: hi_cpufreq_target+0x174/0x474 [hi_pmoc]

which lock already depends on the new lock.
````

依赖链（lockdep 打印为反序 #3 → #0，倒过来读才是真实顺序）：

````
-> #3 (hi_cpufreq_lock):   handle_update → cpufreq_set_policy → cpufreq_userspace_policy_limits
                           → __cpufreq_driver_target → hi_cpufreq_target+0x174
-> #2 (userspace_mutex):   load_module → hi_cpufreq_init → cpufreq_register_driver
                           → cpufreq_online → cpufreq_set_policy+0x288
                           → cpufreq_start_governor → cpufreq_userspace_policy_start
-> #1 (&policy->rwsem):    sysfs write → store+0x78 → down_write()
-> #0 (cpu_hotplug_lock):  hi_cpufreq_target+0x30c → cpus_read_lock()
````

lockdep 给出的结论：

````
Chain exists of:
  cpu_hotplug_lock --> userspace_mutex --> hi_cpufreq_lock

 Possible unsafe locking scenario:
       CPU0                    CPU1
       ----                    ----
  lock(hi_cpufreq_lock);
                               lock(userspace_mutex);
                               lock(hi_cpufreq_lock);
  lock(cpu_hotplug_lock);
 *** DEADLOCK ***
````

**问题定性：**

1. 这是 **lockdep 的"可能环形锁依赖"告警**（possible），说明是 lockdep 基于历史采样画出的锁图推断出的环，不代表此刻已经死锁。
1. 但 "possible" 不等于"无害"——它标志着一条**已被证实存在**的逆序加锁路径，只要并发条件凑齐就是真死锁；而 LTP 热插拔测试 hung 死，恰恰说明这个窗口在真实场景里能被撞到。
1. **违规点非常明确**：驱动私有锁 `hi_cpufreq_lock` 持有期间，又去获取了内核最外层的全局锁 `cpu_hotplug_lock`。

## 二、初步分析排查：

先做现场还原，再谈原因。

### 1) 先分清"已经死了"还是"可能被警告"

第一步永远是看告警之后系统还活动吗：有没有后续 `hung task`、`RCU stall`、`softlockup`、`watchdog` 复位。

* 活动 → 这是一次**预防性告警**，你有时间从容分析；
* 不活动 → 这不是"可能"，要立刻把 hung 之后的日志一并拿出来。

本例属于前者告警 + LTP 场景下 hung 死，说明风险已经实质化，必须修。

### 2) 读日志头部：谁想获得什么锁、已经持有什么锁

````
kworker/3:0/28 is trying to acquire lock:
8102a8a4 (cpu_hotplug_lock){++++}-{0:0}, at: hi_cpufreq_target+0x30c/0x474 [hi_pmoc]
but task is already holding lock:
7f7834e0 (hi_cpufreq_lock){+.+.}-{3:3}, at: hi_cpufreq_target+0x174/0x474 [hi_pmoc]
````

几个读法要点：

* `kworker/3:0/28`：CPU3 上 `events` 工作队列线程，PID 28 —— 说明**触发路径是 workqueue，不是系统调用**；
* `hi_cpufreq_target+0x30c/0x474`：偏移 0x30c，`0x478` 是函数总长；
* `hi_cpufreq_target+0x174`：同一函数内更早的位置；
* 同一个函数里，`+0x174` 先持有了锁，`+0x30c` 又要获取另一把锁 —— **新增的边就是 `hi_cpufreq_lock → cpu_hotplug_lock`**（箭头含义：持左锁时获取右锁）。

顺带说下那串花括号：`{++++}` / `{.+.+}` 是 lockdep 的 usage mask，四个位记录该锁曾在哪些上下文（普通、硬中断、软中断、fs reclaim 等）被获取过，`+` 表示有记录、`.` 表示没有；后面的 `-{3:3}` / `-{0:0}` 是 lockdep 附加的等待类型标记，服务于 wait-type 相关检查。**这两项对本例的"成环"判定都没有影响，可以略过**——成环只看锁的获取顺序。

### 3) 把依赖链"逆序"读

lockdep 打印的 `#3 → #2 → #1 → #0` 标题已说明是 **in reverse order**，倒过来才是它找到的既有路径：

````
cpu_hotplug_lock  →  userspace_mutex  →  hi_cpufreq_lock
````

逐条对应到内核代码路径：

|编号|锁|当时在谁的持有|形成的边|
|--|-|-------|----|
|\#3|`hi_cpufreq_lock`|变频路径持 `userspace_mutex` 时调用 `->target()`|`userspace_mutex → hi_cpufreq_lock`|
|\#2|`userspace_mutex`|模块加载 → `cpufreq_register_driver` 路径启动 governor|`cpu_hotplug_lock → userspace_mutex`|
|\#0|`cpu_hotplug_lock`|当前的 `hi_cpufreq_target+0x30c`|`hi_cpufreq_lock → cpu_hotplug_lock`|

**关键观察**：#2 和 #3 两条边都出自同一个函数 `cpufreq_set_policy` 的两个分支（`+0x288` 走 `start_governor`，`+0x300` 走 `limits`）。这说明 cpufreq core 的*既定锁序*是：

````
cpu_hotplug_lock  >  policy->rwsem  >  userspace_mutex  >  驱动私有锁
    （最外层）                                              （最内层）
````

**当前驱动处在最内层，却获取最外层的锁** —— 这就是逆序的本质。

### 4) 读 "5 locks held"，还原业务触发链

````
#0 (wq_completion)events            ← 工作队列记账，忽略
#1 (&policy->update) work           ← handle_update 这个 work 本身
#2 &policy->rwsem                   ← handle_update+0x34 (down_write)
#3 userspace_mutex                  ← cpufreq_userspace_policy_limits+0x28
#4 hi_cpufreq_lock                  ← hi_cpufreq_target+0x174
（第 6 把，正在获取）cpu_hotplug_lock ← hi_cpufreq_target+0x30c
````

backtrace 是从"被调用者"往"调用者"排的，要从下往上读，得到完整的业务链路：

````
用户态写 cpufreq sysfs 属性（scaling_setspeed）
 → schedule_work(&policy->update)
   → handle_update()                : down_write(&policy->rwsem)
     → cpufreq_set_policy()         : mutex_lock(&userspace_mutex)
       → cpufreq_userspace_policy_limits()
         → __cpufreq_driver_target()
           → hi_cpufreq_target()    : mutex_lock(&hi_cpufreq_lock)   [+0x174]
             → hi_cpufreq_scale()   : cpus_read_lock()               [+0x30c] ← 告警点
````

到这里，**"谁、在什么上下文、按什么顺序获取锁"已经完全清楚了“**。

### 5) 把偏移落到源码行（这一步最关键）

日志给的是偏移，必须落到具体代码行，否则一切分析都是猜。常用三各方式：

````bash
# 最省事：内核源码树自带脚本，支持 func+offset 写法
scripts/faddr2line hi_pmoc.ko hi_cpufreq_target+0x30c
scripts/faddr2line hi_pmoc.ko hi_cpufreq_target+0x174

# 手工方式
nm hi_pmoc.ko | grep -i hi_cpufreq_target
arm-linux-objdump -d --disassemble=hi_cpufreq_target hi_pmoc.ko

# 只有运行时地址（如 0x7f772000）时：先拿模块 .text 加载基址
cat /sys/module/hi_pmoc/sections/.text
# 运行时地址 - 基址 = 段内偏移
````

**这里有个容易卡住的细节**：日志里 `cpus_read_lock()` 的调用帧写的是 `hi_cpufreq_target+0x30c`，可源码里 `cpus_read_lock()` 明明写在 `hi_cpufreq_scale()` 里，为什么栈上看不到 `hi_cpufreq_scale` 这一帧？

答案是**内联**：`hi_cpufreq_scale()` 是 `static`，且整个文件里只被 `hi_cpufreq_target()` 调用一次，GCC 直接把它内联进调用者了。反汇编验证的话，`objdump -d hi_pmoc.ko` 里看不到 `hi_cpufreq_scale` 的独立符号帧，而 `hi_cpufreq_target` 的偏移区间内会同时出现对 `mutex_lock` 和 `cpus_read_lock` 的 `bl` 调用 —— 与日志完全吻合。

定位结果：

````c
static int hi_cpufreq_target(...)
{
    ...
    mutex_lock(&hi_cpufreq_lock);          /* +0x174 */
    ...
    if (cpu_dvfs_enable)
        ret = hi_cpufreq_scale(policy, current_target_freq, policy->cur);  /* 在锁内调用 */
    mutex_unlock(&hi_cpufreq_lock);
}

static int hi_cpufreq_scale(...)
{
    ...
    cpus_read_lock();                      /* 内联后落在 +0x30c */
    ...
    cpus_read_unlock();
}
````

即：**`cpus_read_lock()` 全程在 `hi_cpufreq_lock` 的保护之下获取**，锁序确凿：`hi_cpufreq_lock → cpu_hotplug_lock`。

### 6) 确认 lockdep 校验确实开着

````bash
zcat /proc/config.gz | grep PROVE_LOCKING   # CONFIG_PROVE_LOCKING=y
ls /proc/lockdep                            # 存在即 lockdep 已启用
````

开着是好事——这类问题在没开 lockdep 的设备上只会以"偶发 hung 死"的形式出现，日志里什么都不会留下，到时候排查成本要高一个数量级。

## 三、深入分析原因

### 1) 逆序的真正含义：驱动在最内层，却去获取最外层

cpufreq core 的调用约定是：`->target()` / `->target_index()` 回调**运行在 `policy->rwsem` 之下**（core 持有该读写信号量后才调用驱动）。也就是说，驱动回调天生处于锁层级的最内层。

而 `cpu_hotplug_lock` 是整个内核最外层的全局锁之一（保护 CPU online mask）。**在最内层回调里获取最外层锁，等于主动制造逆序**。

### 2) 真正的原因：锁保护的临界代码，已被改变，不再需要保护。

顺着 `hi_cpufreq_scale()` 的历史一路追溯，才能解释"为什么会有一把莫名其妙的 hotplug 锁"。

**老内核（≤ v3.14）为什么需要它？** 当时的版本 `struct cpufreq_freqs` 里有个 `.cpu` 成员，驱动要自己遍历 online CPU 逐个发通知：

````c
for_each_online_cpu(freqs.cpu)              /* 老写法 */
    cpufreq_notify_transition(policy, &freqs, CPUFREQ_PRECHANGE);
或是：
for_each_cpu(freqs.cpu, policy->cpus)
    cpufreq_notify_transition(policy, &freqs, CPUFREQ_POSTCHANGE);
````

**遍历 online CPU 掩码时，必须防止 CPU 上下线修改这个掩码** —— 于是配套一把 `get_online_cpus()`锁。**锁和循环是配套的。**
这类"保护对象已消失的空锁"，是老驱动移植里最常见的一类技术债：编译得过、跑得起来、只有在开启 lockdep 且并发场景凑齐时才现形。

### 3) 死锁窗口为什么是"CPU 热插拔"

lockdep 那张 CPU0/CPU1 图是抽象推演，真实死锁需要三个条件并发：

1. 线程 A 持 `hi_cpufreq_lock` 等 `cpu_hotplug_lock`（本例变频路径，**常见**）；
1. 线程 B 持 `userspace_mutex` 等 `hi_cpufreq_lock`（另一核也在变频，**常见**）；
1. `cpu_hotplug_lock` 的持有者在等 `userspace_mutex`（**只在 cpufreq 驱动注册/注销、或 CPU hotplug 时出现，罕见**）。

第 3 条是稀有条件，这也解释了为什么平时运行好好的。而 **LTP 的 CPU 热插拔用例正好在持续制造第 3 条**：CPU 下线/上线时，core 会在持有 `cpu_hotplug_lock` 的状态下走 `cpufreq_online/offline` → `cpufreq_set_policy` → governor 的 start/stop（取 `userspace_mutex`），这条边在 lockdep 的 #2 号栈里已经明明白白地打印出来了。

**换句话说：热插拔不是碰巧撞上的，而是唯一能稳定凑齐三个条件的场景。** 开机阶段 `modprobe hi_pmoc` 与用户态写 `scaling_setspeed` 并发，是另一个高危窗口。

## 四、修复策略：

### 1) 先立规则，再谈改法

有一条硬规则必须先摆出来：

 > 
 > **cpufreq 的 `->target()` 回调运行在 `policy->rwsem` 之下，回调内部不应再获取 `cpu_hotplug_lock`。**

理由有三：

* core 已经通过 `policy->rwsem` 完成了变频路径的串行化；
* CPU hotplug 的互斥由 core 侧（`cpufreq_cpu_get()`、hotplug 回调）在进入驱动之前处理；
* 通知链（`transition_begin/end`）自身已涵盖所需的 CPU 状态同步。

### 2) 方案对比

|方案|做法|评价|
|--|--|--|
|A. 调整锁序|把 `hi_cpufreq_lock` 挪到 `cpus_read_lock()` 之后，或在 target 外先获取hotplug 锁|**不可行**。逆序的本质没变（还是在同一条路径上同时持有两把锁），而且会把驱动私有锁的范围扩大到整个变频流程，引入新的串行化瓶颈|
|B. 换保护方式|用 `policy->cpus` 掩码替代 online mask 遍历|**不需要**。遍历循环早已删除，没有要保护的对象|
|C. 直接删除锁对|删掉 `cpus_read_lock()/cpus_read_unlock()`|**采纳**。保护对象已消失，删掉即消除违规边，且无功能损失|

### 3) 判定方法：先问"保护什么"，再问"还在不在"

这套判定流程比"看到告警就调锁序"要可靠得多：

1. **这把锁当初是为什么加的？** —— 保护 `for_each_online_cpu` 遍历 online mask 期间 CPU 不上下线。
1. **它保护的对象现在还在吗？** —— 循环已被 `cpufreq_freq_transition_begin/end` 取代并删除，**不在了**。
1. **删掉它，剩下的代码还需要同步保护吗？** —— `transition_begin/end` 内部负责串行化与通知；`hi_device_scale()` 是寄存器级操作；`hi_cpufreq_getspeed()` 读硬件频率，均与 CPU 在线状态无关。**不需要。**
1. **结论**：删除，且不引入替代锁。

### 4) 最终补丁

**注意条件编译的对称性**——这是跨版本驱动移植的重点：这份源码同时要支持老的 3.18 SDK 和新的 5.15，所以**只删 5.15 分支的 `cpus_read_lock()`，`< 4.13` 分支的 `get_online_cpus()` 必须保留**，因为那条分支上 `for_each_online_cpu` 循环还在，锁与循环仍然配套。**"删一半"不是偷懒，而是精准匹配各自分支的保护需求。**

源码清单参考“其它细节”

### 5) 全局排查同类逆序

**lockdep 只在第一次见到某条边时打印，所以"只报一次"绝不等于"只有一处"。** 删完之后务必全模块扫描：

````bash
grep -rn "hi_cpufreq_lock\|cpus_read_lock\|get_online_cpus\|cpus_write_lock" drivers/msp/pm/
````

重点看 `init` / `exit` / `suspend` / `resume` / 各类 notifier 回调里有没有同样的逆序模式，以及 `hi_cpufreq_lock` 是否在别处包住了其他大锁。

## 五、修复后测试：

### 1) 先把复现路径固化下来

修之前就要想清楚"怎么证明它好了"。针对本例，把触发条件固化成一个固定序列，修前必现、修后必不现：

````
开机 → modprobe hi_pmoc（触发 cpufreq_register_driver 路径）
     → 切换 governor 为 userspace
     → 写 sysfs scaling_setspeed（触发变频 workqueue 路径）
     → CPU offline / online 反复上下线（制造 hotplug 侧并发）
     → 系统休眠 / 唤醒
````

其中"变频"与"热插拔"**并发**是这个 case 的灵魂，单独跑任何一半都不会复现。

### 2) LTP CPU 热插拔测试：通过

修复后重跑 LTP 的 CPU 热插拔用例，**不再 hung 死**，这是最直接的验收标准——毕竟问题最初就是被它逼出来的。建议多轮次、多轮持续时间跑（而非单轮），因为并发窗口本身带随机性。

### 3) lockdep：告警消失，且无新边

* 原 `possible circular locking dependency detected` 告警**不再出现**；
* 沿完整复现路径跑完后，确认 lockdep **没有吐出新的边**（删除一把锁有时会暴露被它掩盖的另一条路径，这一步不能省）；
* 确认内核仍为 `Not tainted`，无 `hung task` / `RCU stall` / `softlockup` / `watchdog` 复位。

### 4) 功能回归：变频本身要真的正常

"不告警"不等于"功能对"，还要验证变频链路完好：

* 写 `scaling_setspeed` 后，用 `hi_cpufreq_getspeed()` / `cpufreq` sysfs 读回的**实际频率确实变化**；
* 升频 / 降频双向、跨多个频点都试一遍；
* 通知链消费者工作正常：`cpufreq_stats` 能统计到切换、`loops_per_jiffy` 校准无异常（这两项也正是 `freqs.policy` 填对、`transition_failed` 传对之后才可能正确的部分）；
* 刻意构造一次切换失败，确认核心走了 `swap(old, new)` 补发路径，通知链回到一致状态（这是顺带修的那处逻辑错误的验收点）。

### 5) 稳定性与跨版本回归

* 长跑（变频 + 热插拔 + 负载）观察；
* 回到老的 3.18 SDK 上回归，确认 `<4.13` 分支保留的 `get_online_cpus()` 未被误删、老内核行为不变。

### 6) 经验沉淀

回到移植本身，这次踩坑可以提炼成三条可复用的经验：

1. **移植不是"改到能编译"，而是"改到语义等价"。** API 换了名字（`get_online_cpus` → `cpus_read_lock`）、结构体换了成员（`.cpu` → `.policy`）、机制换了实现（自遍历通知 → 核心统一通知），每一处都要回头问一句：**与它配套的那些代码，还成立吗？** 本例中循环删了锁没删，就是配套关系断裂的直接后果。
1. **给不同 API 的版本阈值建一张表。** 3.15（通知）、4.13（hotplug 锁更名）、5.2（freqs.policy）、5.15（老 API 删除）——混用阈值是跨版本驱动里最高发的错误，而且往往静默。
1. **让 lockdep 一直开着，并且用 LTP 这类工具去制造并发。** 这次的问题在常规功能测试里几乎不会现形，是 `CONFIG_PROVE_LOCKING` + CPU 热插拔压力把它逼出来的。**锁序问题从来不是"测功能"能测出来的，只有"测并发"才行。**

## 其它细节
