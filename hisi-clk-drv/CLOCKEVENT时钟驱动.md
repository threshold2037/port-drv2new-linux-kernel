## 背景介绍

         HiSTBLinuxV100R005C00SPC041B020版本的SDK是基于linux-3.18内核，比较旧。基于hi3798mv100硬件平台，
    把HiSTBLinuxV100R005C00SPC041B020版本的驱动移植到linux-5.15内核上。使用buildroot创建工具链，和根文件系统。
    全部代码的移植工作基本完成，编译通过。到了将代码放到目标硬件实际运行的阶段。
    
    drivers/hisilicon/clocksource/timer.c驱动程序移植到linux-5.15内核，源码先按linux-5.15内核作了初步适配，比如不同版本带来
    的变量或宏采用以下替换：
    //       linux-3.18                                        linux-5.15
    #define clock_event_mode                               clock_event_state
    
    // emu clock_event_mode {          
    	#define CLOCK_EVT_MODE_PERIODIC                    CLOCK_EVT_STATE_PERIODIC
    	#define CLOCK_EVT_MODE_ONESHOT                     CLOCK_EVT_STATE_ONESHOT
    	#define CLOCK_EVT_MODE_UNUSED                      CLOCK_EVT_STATE_DETACHED                
    	#define CLOCK_EVT_MODE_SHUTDOWN                    CLOCK_EVT_STATE_SHUTDOWN
    // };
    
    #define CPU_DYING                                       CPU_DEAD_FROZEN
    #define CLOCKSOURCE_OF_DECLARE                          TIMER_OF_DECLARE
    
    extern int setup_irq(int,struct irqaction *);
    extern int remove_irq(int,struct irqaction *);
    extern int register_cpu_notifier(struct notifier_block *);
    

## 一、问题描述

    1、编译通过：
    	CC      drivers/hisilicon/clocksource/timer.o   没有报错信息。
    2、链接报错：
    	arm-hisi-linux-gnueabi-ld: drivers/hisilicon/clocksource/timer.o: in function `hisi_local_timer_setup':
    		drivers/hisilicon/clocksource/timer.c:332: undefined reference to `setup_irq'
    	arm-hisi-linux-gnueabi-ld: drivers/hisilicon/clocksource/timer.o: in function `hisi_local_timer_stop':
    		drivers/hisilicon/clocksource/timer.c:367: undefined reference to `remove_irq'
    	arm-hisi-linux-gnueabi-ld: drivers/hisilicon/clocksource/timer.o: in function `hisi_local_timer_register':
    		drivers/hisilicon/clocksource/timer.c:512: undefined reference to `register_cpu_notifier'
    

## 二、初步分析排查：

    1、初步判断：setup_irq，remove_irq，register_cpu_notifier 三个函数在linux-5.15内核可能已经移除或不再导出符号。
    2、查阅权威信息：
    	1）、elixir网上查阅linux-3.18内核，setup_irq和remove_irq函数在include/linux/irq.h文件定义 (as a prototype)， 
    		register_cpu_notifier函数在include/linux/cpu.h文件定义(as a prototype)。
    	
    	2）、elixir网上查阅linux-5.15内核，setup_irq和remove_irq函数在内核文件没有定义，register_cpu_notifier函数在内核文件没
    	有定义。
    	
    	3）、elixir网上进一步查阅，setup_irq和remove_irq函数在linux-5.7以上的内核被移除了。
    	
    	4）、elixir网上进一步查阅，register_cpu_notifier函数在linux-4.10以上的内核被移除了。
    
    	5）、在LKML上查找“Remove setup_irq”，找到有关tip: irq/urgent genirq: Remove setup_irq() and remove_irq()，点进去。
    	找到Commit-ID和Gitweb关键字。点Gitweb后面的网址，里面有这样的描述：“Now that all the users of setup_irq() & 
    	remove_irq() have been replaced by request_irq() & free_irq() respectively, delete them.”
    
    	 6）、用同样的方法找到register_cpu_notifier函数的替代函数，cpuhp_setup_state() + 分别提供 startup 和 teardown 两个回调。
    

## 三、改写源码思路：

    1、改写原hisi_set_mode函数：
    	原hisi_set_mode函数包含设置四种模式：CLOCK_EVT_MODE_PERIODIC、CLOCK_EVT_MODE_ONESHOT、CLOCK_EVT_MODE_SHUTDOWN、
    	CLOCK_EVT_MODE_UNUSED。linux-5.15内核没有完全对应的CLOCK_EVT_MODE_UNUSED模式，舍去。
    	用hisi_clkevt_set_state_periodic、hisi_clkevt_set_state_oneshot、hisi_clkevt_set_state_shutdown分别实现前三种模
    	式的函数代替。
    
    2、改写原hisi_local_timer_setup函数：
    	原hisi_local_timer_setup函数中clk->set_mode = hisi_set_mode;改成：
    		hisi_evt->evt.set_state_periodic = hisi_clkevt_set_state_periodic;
    		hisi_evt->evt.set_state_oneshot = hisi_clkevt_set_state_oneshot;
    		hisi_evt->evt.set_state_shutdown = hisi_clkevt_set_state_shutdown;
    	
    	原hisi_local_timer_setup函数中setup_irq(clk->irq, action)改成：
    		request_irq(hisi_evt->evt.irq, "action里的参数")
    	并以hisi_local_timer_startup命名。
    
    3、改写原hisi_local_timer_stop函数：
    	原hisi_local_timer_stop函数中remove_irq(clk->irq, this_cpu_ptr(hisi_event_irq));改成：
    		free_irq(hisi_evt->evt.irq, hisi_evt);
    	并以hisi_local_timer_teardown命名。
    
    4、舍弃原hisi_local_timer_cpu_notify函数：
    	原hisi_local_timer_cpu_notify函数中实现的两个分支，CPU_STARTING中调用hisi_local_timer_setup函数，CPU_DYING中调用
    	hisi_local_timer_stop。
    	 且原来将hisi_local_timer_cpu_notify 函数注册为 CPU 热插拔通知链（.cpu_notifier）的回调函数：
    		static struct notifier_block hisi_local_timer_cpu_nb = {
    		    .notifier_call = hisi_local_timer_cpu_notify,
    		};舍弃。
    
    5、修改hisi_local_timer_register函数：
    	原hisi_local_timer_register函数中register_cpu_notifier(&hisi_local_timer_cpu_nb);改成：
    		hisi_timer_hp_state = cpuhp_setup_state_nocalls(CPUHP_AP_ONLINE_DYN,
    											                "hisi/timer:online",
    											                hisi_local_timer_startup,
    											                hisi_local_timer_teardown);
    	 回调函数作为函数参数传递。
    

## 四、最终源码

    略
    

## 五、效果演示

    1、启动信息输出：
    	[    0.000000] clocksource: hisi-timer: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 79635851949 ns
    	[    0.000002] sched_clock: 32 bits at 24MHz, resolution 41ns, wraps every 89478484971ns
    						......
    	Calibrating delay loop... 2371.58 BogoMIPS (lpj=1185792)
    						......
    	[    0.067094] /cpus/cpu@0 missing clock-frequency property
    	[    0.072547] /cpus/cpu@1 missing clock-frequency property
    	[    0.077949] /cpus/cpu@2 missing clock-frequency property
    	[    0.083365] /cpus/cpu@3 missing clock-frequency property
    	[    0.088751] CPU0: thread -1, cpu 0, socket 0, mpidr 80000000
    						......
    	[    0.121173] smp: Bringing up secondary CPUs ...
    	[    0.135977] CPU1: thread -1, cpu 1, socket 0, mpidr 80000001
    	[    0.150977] CPU2: thread -1, cpu 2, socket 0, mpidr 80000002
    	[    0.165978] CPU3: thread -1, cpu 3, socket 0, mpidr 80000003
    	[    0.166232] smp: Brought up 1 node, 4 CPUs
    	[    0.176134] SMP: Total of 4 processors activated (9560.06 BogoMIPS).
    	[    0.182559] CPU: All CPU(s) started in SVC mode.
    						......
    	[    0.242927] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 1911260446275000 ns
    
    2、指令查看
    	cat /proc/timer_list | grep "event_handler"
    	 		event_handler:  tick_handle_oneshot_broadcast
    	 		event_handler:  hrtimer_interrupt
    	 		event_handler:  hrtimer_interrupt
    	 		event_handler:  hrtimer_interrupt
    	 		event_handler:  hrtimer_interrupt
    	
    	cat /sys/devices/system/clocksource/clocksource0/available_clocksource
    			hisi-timer
    	cat /sys/devices/system/clocksource/clocksource0/current_clocksource
    			hisi-timer
    3、测试：
    	用内核函数debugfs_create_file写一个测试用例hrtimer_test。测试数据如下：
    	
       echo 1 > hrtimer_test
     	cat hrtimer_test
    		1 usecs x 100: exp=1000 allowed=995 min=31625 avg=33719 max=96708
    	
     	echo 10 > hrtimer_test
     	cat hrtimer_test
    		10 usecs x 100: exp=10000 allowed=9950 min=30958 avg=32529 max=77583
    	
     	echo 100 > hrtimer_test
     	cat hrtimer_test
    		100 usecs x 100: exp=100000 allowed=99500 min=122750 avg=128420 max=158875
    	
     	echo 1000 > hrtimer_test
     	cat hrtimer_test
    		1000 usecs x 100: exp=1000000 allowed=995000 min=1030542 avg=1033695 max=1061625
    
    4、 jiffies定时器的精度，通常在10mS。hrtimer实测达到40uS
    

## Support

若本文对你的学习与工作有所帮助、启发，欢迎支持！  
[SupportQR](../Support/SupportQR.md)

## 其它细节
