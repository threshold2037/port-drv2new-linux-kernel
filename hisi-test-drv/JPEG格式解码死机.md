## 背景介绍：

    驱动程序能加载成功，不等于它就正常运行，只有通过测试才能把工作做得更扎实。
    
       先测试了最基础的/dev/fb0,正常显示了蓝、红、绿、黄、白色块。证明基础的驱动程序 ddr.ko、hi_media.ko、hi_mmz.ko、
       hi_common.ko、hi_pq.ko正常，hi_hdmi.ko、hi_fb.ko、hi_vou.ko驱动及所对应的硬件是正常工作的。也验证了
    

《[gpu的中断号问题](../hisi-gpu-drv/gpu%E7%9A%84%E4%B8%AD%E6%96%AD%E5%8F%B7%E9%97%AE%E9%A2%98.md) 》中使用的硬件中断号转化为虚拟中断号注册是正确的。

````
紧接着测试了/dev/tde，正常显示。TDE（Two-Dimensional Graphics Engine，二维图形引擎）展示了2D图像处理的“YUV 色彩空间到 RGB 色彩空间的转换”、“图像混合（Blending）”、“颜色填充（Color Fill）”、“颜色键控（Color Key）”、“去闪烁（De-flicker）”、“快速拷贝（Quick Copy）”、“图像缩放（Resize）”等功能。
```	
	经过这两种测试例程后，我们来看看硬件中断的情况：
	root@histb:~/sample/tde# cat /proc/interrupts  |  grep -E 'hi_vdp_irq | hi_tde_irq'
		 35:     321093          0          0          0     GIC-0 122 Level     hi_vdp_irq
		 36:      0             23          0          0     GIC-0 123 Level     hi_tde_irq
	
	从上面指令中看到第1列“虚拟中断号”，第2——5列“中断次数计数”，第7列“硬件中断号”，第9列“驱动程序名称”。
	 

## 一、问题描述：
	执行测试例程输出信息如下：
```shell
root@histb:~/sample/higo# ./sample_dec
		 --- Get HDMI event: HOTPLUG. ---
		HIGO Version            :4.0.0.0 SPC040 RELEASE
		HIGO Build Time         :Sep  2 2016 15:47:47
		HIGO Adp Version        :4.0.0.0 V1R2&V1R3&V1R5&V1R7 SPC040
		HIGO Adp Build Time     :Sep  2 2016 15:47:49
````

    输入没有响应，不能中止程序。几分钟后，输出信息如下：
    

````shell
[  171.639602] rcu: INFO: rcu_sched detected stalls on CPUs/tasks:
[  171.645575] rcu:     2-...0: (6 ticks this GP) idle=401/1/0x40000000 softirq=8400/8403 fqs=15000
[  171.654222]  (detected by 3, t=60016 jiffies, g=14073, q=34)
[  171.659900] Sending NMI from CPU 3 to CPUs 2:
[  181.648668] rcu: rcu_sched kthread timer wakeup didn't happen for 10007 jiffies! 
			g14073 f0x0 RCU_GP_WAIT_FQS(5) ->state=0x402
[  181.659993] rcu:     Possible timer handling issue on cpu=3 timer-softirq=27524
[  181.667052] rcu: rcu_sched kthread starved for 10029 jiffies! g14073 f0x0 RCU_GP_WAIT_FQS(5) ->state=0x402 ->cpu=3
[  181.677421] rcu:     Unless rcu_sched kthread gets sufficient CPU time, OOM is now expected behavior.
[  181.686388] rcu: RCU grace-period kthread stack dump:
[  181.691445] task:rcu_sched       state:I stack:    0 pid:   12 ppid:     2 flags:0x00000000
[  181.699829] Backtrace: 略
````

## 二、初步分析排查：

    1、初步判断：
    	这是一个典型的 RCU Stall（RCU 停滞）故障，具体表现为 RCU kthread 饥饿（starvation）。
    
    2、关键信息：
    	rcu: rcu_sched kthread starved for 10029 jiffies! g14073 f0x0 RCU_GP_WAIT_FQS(5) ->state=0x402 ->cpu=3
    RCU调度kthread已被饿死（starved）10029个jiffies，即长时间未获得CPU时间。该kthread本身运行在CPU 3上，但CPU 3因其他任务
    导致kthread无法被调度。
    
    3、使用strace工具跟踪：
    	root@histb:~/sample/higo# strace -o sample_dec_strace.log ./sample_dec。同样死机。重启后查看sample_dec_strace.log
    	文件内容。信息如下：
    	root@histb:~/sample/higo# cat sample_dec_strace.log | tail -2
    		ioctl(14, _IOC(_IOC_WRITE, 0x74, 0x9, 0x10), 0x6ecb48d4) = 0
    		clock_nanosleep_time64(CLOCK_REALTIME, 0, {tv_sec=3, tv_nsec=0},
    	从上面的信息看出来，死机的原因不一定是休眠函数对系统定时器调用，但卡住的地方确实是和定时器clock_nanosleep_time64(...}相关。
    
    	root@histb:~/sample/higo# cat sample_dec_strace.log | grep -E 
    		'openat.*3|openat.*4|openat.*9|openat.*11|openat.*14|openat.*15'
    		openat(AT_FDCWD, "/lib/libhigo.so", O_RDONLY|O_LARGEFILE|O_CLOEXEC) = 3
    			......
    		openat(AT_FDCWD, "/lib/libhigoadp.so", O_RDONLY|O_LARGEFILE|O_CLOEXEC) = 3
    		openat(AT_FDCWD, "/dev/hi_log", O_RDWR|O_NONBLOCK) = 4
    		openat(AT_FDCWD, "/dev/hi_disp", O_RDWR|O_NONBLOCK|O_LARGEFILE) = 9
    		openat(AT_FDCWD, "/dev/hi_hdmi", O_RDWR|O_LARGEFILE) = 11
    		openat(AT_FDCWD, "/dev/hi_tde", O_RDWR|O_LARGEFILE) = 14
    		openat(AT_FDCWD, "/usr/lib/higo-adp/decoder", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_CLOEXEC|O_DIRECTORY) = 15
    		openat(AT_FDCWD, "/dev/fb0", O_RDWR)    = 15
    	打开库文件和设备文件都没有报错。
    	
    	root@histb:~/sample/higo# cat sample_dec_strace.log | grep 'ioctl'
    		ioctl(4, _IOC(_IOC_READ, 0x3, 0, 0x4), 0x6ecb4a14) = 0
    		ioctl(9, _IOC(_IOC_NONE, 0x45, 0x2, 0), 0x1) = 0
    			......
    		ioctl(9, _IOC(_IOC_WRITE, 0x22, 0x2, 0x4), 0x6ecb4a0c) = 0
    		ioctl(11, _IOC(_IOC_READ|_IOC_WRITE, 0x23, 0x1, 0x4), 0x6ecb49e0) = 0
    			......
    		ioctl(11, _IOC(_IOC_READ|_IOC_WRITE, 0x23, 0x3, 0xc), 0x6ecb49e8) = 0
    		ioctl(12, _IOC(_IOC_READ|_IOC_WRITE, 0x6d, 0xa, 0x3c), 0x6ecb49a0) = 0
    			......
    		ioctl(12, _IOC(_IOC_READ|_IOC_WRITE, 0x6d, 0xa, 0x3c), 0x6ecb47e8) = 0
    		ioctl(14, _IOC(_IOC_WRITE, 0x74, 0x15, 0x4), 0x6ecb4a4c) = 0
    			......
    		ioctl(14, _IOC(_IOC_WRITE, 0x74, 0x9, 0x10), 0x6ecb48d4) = 0
    		ioctl(15, FBIOGET_VSCREENINFO, 0x6ecb4568) = 0
    			......
    		ioctl(15, _IOC(_IOC_READ, 0x46, 0x7b, 0x24), 0x6ecb4854) = 0
    	对设备文件的读写控制指令也都没有报错。看起来一切正常。
    
    4、查看源码：
    	cat sample_dec.c | grep -En 'main|sleep\(|usleep\('
    		119:HI_S32 main(HI_S32 argc, HI_CHAR* argv[])
    		202:    sleep(3);
    		217:                sleep(1);
    		225:        usleep(200 * 1000);
        仔细分析源程序，这些休眠函数并不是起决定性作用的，试着注释它们。试看看会卡死在哪个程序上，排除休眠函数的干扰。改源
        程序，编译，重新加载程序。再次执行root@histb:~/sample/higo# strace -o fix_sample_dec_strace.log ./sample_dec，
        同样卡死，几分钟后死机。
    	cat fix_sample_dec_strace.log | tail -30，输出信息为空。没有能够保存有信息。
    
    5、使用其它工具的可能性：
    	strace工具：   功能受限，不能定位问题。
    	ltrace工具：    也是一样的，只能定位到sample_dec例程在用户空间的最后一个函数，也定位不到具体的内核位置。
    	GDB工具：      因为sample_dec例程会调用libhigoadp.so库文件，再由库进行内核的系统调用，库文件没有源码的，跟踪不下去。
    	dmesg工具：   在死机的时候操作不了，重启后数据会覆盖，也没有作用。
    	pstore工具：    是在panic()函数调用时才会记录下来信息，目前的故障死机并没有发生panic。
    	journalctl：      开发板没有配置，估计卡死瞬间，journalctl的守护进程也没有办法获得CPU控制权，把信息写入日志。
    到此，走入死胡同了。
    
    6、HiSTBLinuxV100R005C00SPC041B020版测试例程回溯：
        测试原来的linux3.18内核的SDK里的sample，看看是不是驱动从3.18移植到5.15内核才带来的问题。经过测试，原来的linux3.18内核，
    版本HiSTBLinuxV100R005C00SPC041B020也存在同样的问题，且同样是sample_dec例程。看来这是个遗留问题！！
    
    7、发现故障的规律：
      经过多次测试，发现无论是HiSTBLinuxV100R005C00SPC041B020版SDK，还是移植到5.15内核的，都存在以下规律：sample/higo目录下
     的sample_animation、sample_encoder、sample_gdev、sample_surface  sample_wm、sample_bitmapfont、sample_fillrect、
     sample_logo、sample_text正常。但是sample_dec 、sample_performance、 sample_effect、sample_stereo会死机。查看所有死机的
     测试例程，无一例外的使用了JPEG图片格式。大胆猜测是hi_jpeg.ko驱动有问题。
    
    8、分析JPEG驱动程序：（在宿主机上执行）
    find ./source -type d -name 'jpeg'
    	./source/msp/drv/jpeg
    	./source/msp/api/jpeg
    找到hi_jpeg.ko驱动的源码目录，按驱动调用链：sample_dec——>libhigoadp.so库——>open(......，"/dev/hi_jpeg"，......）——>ioctl
    ——>hi_jpeg.ko，猜测./source/msp/drv/jpeg目录下的源码可能会有对应的ioctl函数。
    
    grep -r '.*ioctl.*' ./source/msp/drv/jpeg
    	./.../jpeg/src/jpeg_drv_osr.c:#include <linux/ioctl.h>
    	./.../jpeg/src/jpeg_drv_osr.c:static long jpg_osr_ioctl(struct file *file, HI_U32 Cmd, unsigned long Arg);
    	./.../jpeg/src/jpeg_drv_osr.c:static long jpg_osr_compat_ioctl(struct file *file, HI_U32 Cmd, unsigned long Arg);
    	./.../jpeg/src/jpeg_drv_osr.c:                                 jpg_osr_ioctl,jpg_osr_compat_ioctl,
    	./.../jpeg/src/jpeg_drv_osr.c:                                 jpg_osr_ioctl,NULL,NULL, NULL);
    	./.../jpeg/src/jpeg_drv_osr.c:* func            : jpg_osr_ioctl
    	./.../jpeg/src/jpeg_drv_osr.c:static long jpg_osr_ioctl(struct file *file, HI_U32 Cmd, unsigned long Arg)
    	./.../jpeg/src/jpeg_drv_osr.c:* func          : jpge_compat_ioctl
    	./.../jpeg/src/jpeg_drv_osr.c:static long jpg_osr_compat_ioctl(struct file *file, HI_U32 Cmd, unsigned long Arg)
    	./.../jpeg/src/jpeg_drv_osr.c:    return jpg_osr_ioctl(file,Cmd,Arg);
    	找到关键的jpg_osr_ioctl（）函数。
    	
    查看jpg_osr_ioctl（）函数的关键代码:
    sed -n '1120,1122p;1136,1137p' ./src/jpeg_drv_osr.c
    	static long jpg_osr_ioctl(struct file *file, HI_U32 Cmd, unsigned long Arg)
    	{
    	    HI_U8 u8Cmd = _IOC_NR(Cmd);
    		    ......
    	    return gs_DrvJpegCtlFunc[u8Cmd].DrvJpegIoctlFunc(Arg);
    	}
    gs_DrvJpegCtlFunc[u8Cmd].DrvJpegIoctlFunc(Arg);执行的就是u8Cmd对应的函数。
    
    显示关键代码：sed -n '159,169p' ./src/jpeg_drv_osr.c
    	static DRV_JPEG_IOCTLFUNC_ITEM gs_DrvJpegCtlFunc[DRV_JPEG_IOCTLFUNC_ITEM_NUM_MAX] = {
    	     {CMD_JPG_GETDEVICE, JPEG_OSR_GetDevice},        {CMD_JPG_SUSPEND,    JPEG_OSR_Suspend},
    	     {CMD_JPG_RESUME,    JPEG_OSR_Resume},           {CMD_JPG_GETSUSPEND, JPEG_OSR_GetSuspend},
    	     {CMD_JPG_GETRESUME, JPEG_OSR_GetResume},        {CMD_JPG_RESET,      JPEG_OSR_Reset},
    	     {CMD_JPG_CANCEL_RESET, JPEG_OSR_CancelReset},   {CMD_JPG_OPEN_RESET_CLOCK, JPEG_OSR_ResetClock},
    	     {CMD_JPG_GETINTSTATUS, JPEG_OSR_GetIntStatus},  {CMD_JPG_GETRESUMEVALUE, JPEG_OSR_GetResumeValue},
    	     {CMD_JPG_READPROC, JPEG_OSR_ReadProc},          {CMD_JPG_CREATEDEC, JPEG_OSR_CreateDec},
    	     {CMD_JPG_DECINFO, JPEG_OSR_DecInfo},            {CMD_JPG_DECOUTINFO, JPEG_OSR_DecOutInfo},
    	     {CMD_JPG_DECODE,  JPEG_OSR_Decode},             {CMD_JPG_DESTORYDEC, JPEG_OSR_DestoryDec},
    	     {CMD_JPG_GETLUPIXSUM, JPEG_OSR_GetLuPixSum},    {CMD_JPG_LOWDELAY_LINEINFO, JPEG_OSR_LowdelayLineInfo},
    	     {CMD_JPG_SET_LOWDELAY_LINE, JPEG_OSR_SetLowdelayLine},  {0,NULL}
    
    9、添加printk输出信息：
       trace工具并没有跟踪到有/dev/gpeg的设备，也没办法确定是在哪一个命令上死机了。哪个命令是最有可能首先执行呢？按一般规律，任何
     需要独占访问、有状态或需要初始化的硬件外设，在使用前都必须经过一个“获取设备并使其就绪”的步骤。就有可能的
    就是JPEG_OSR_GetDevice函数了。
        
      显示并分析关键代码：
    	sed -n '1191,1195p;1201p;' ./src/jpeg_drv_osr.c
    		static HI_S32 JPEG_OSR_GetDevice(HI_ULONG arg)
    		{
    			HI_S32 Ret = HI_SUCCESS;
    			Ret = JPEG_DRV_GetDevice();
    				......
    		}
    	sed -n '1169,1170p;1180,1185p;1188p' ./src/jpeg_drv_osr.c
    		HI_S32 JPEG_DRV_GetDevice(HI_VOID)
    		{
    			DRV_JPEG_ResetReg();
    			DRV_JPEG_OnClock();
    			DRV_JPEG_CancelReset();
    			JPEG_DRV_SetDecState(HI_TRUE);
    		}
    在函数JPEG_DRV_GetDevice()内部的
    DRV_JPEG_ResetReg();DRV_JPEG_OnClock();DRV_JPEG_CancelReset();JPEG_DRV_SetDecState(HI_TRUE);
    语句前都加入printk()打印语句。就能确定是死机在哪一个语句上了。实测就发生在DRV_JPEG_ResetReg();执行时就死机了。找到死机的
    具体位置了。
    

## 三、进一步精确定位：

    1、DRV_JPEG_ResetReg()就是对硬件复位，往往还有时钟使能，时钟频率选择等其它功能。查阅硬件手册，得到JPGD的寄存器
    首地址是0xf8c40000。
    	用工具软件himm：
    root@histb:~/sample# himm 0xf8c40000                        root@histb:~/sample# himm 0xf8c70000
    	*** Board tools : ver0.0.1_20130123  ***                    *** Board tools : ver0.0.1_20130123  ***
    	[debug]: {source/utils/cmdshell.c:166}cmdstr:himm           [debug]: {source/utils/cmdshell.c:166}cmdstr:himm
    	====dump memory 0XF8C40000====                               ====dump memory 0XF8C70000====
                                                                    0xf8c70000: 0x00000000
    	                                                            NewValue:0x00000000
    	                                                            [END]                          
    0xf8c40000读取会死机，而读取PGD的寄存器首地址0xf8c70000不会死机。
    查阅硬件手册，与JPGD相对应PERI_CRG31的地址是0xf8a2207c。与PGD相对应PERI_CRG34的地址是0xf8a22084。
    	root@histb:~# himm 0xf8a2207c                                root@histb:~# himm 0xf8a22084
    		*** Board tools : ver0.0.1_20130123  ***                       *** Board tools : ver0.0.1_20130123  ***
    		[debug]: {source/utils/cmdshell.c:166}cmdstr:himm              [debug]: 
    		{source/utils/cmdshell.c:166}cmdstr:himm
    		====dump memory 0XF8A2207C====                                  ====dump memory 0XF8A22084====
    		0xf8a2207c: 0x00000010                                          0xf8a22084: 0x00000010
    		NewValue:0x00000010                                             NewValue:0x00000010
    		[END]                                                           [END]
    查阅硬件手册，0x00000010表示的状态是时钟没有使能，处于复位状态。两者都是相同的状态，JPGD寄存器地址读写会死机，PGD寄存器地址
    读写正常。这样就能完全解释为什么只要有JPEG解码器的测试例程都死机的原因：JPEG解码硬件有它特定的初始化逻辑，与其它几种格式的解
    码器的初始化逻辑不一样。不能按照能用的初始化去适配它。
    
    2、修复方案：给JPEG解码器的JPGD寄存器写一段专门的初始化程序，与BPD寄存器、PGD寄存器不能通用。
    

## 四、修复程序：

    static HI_VOID JPEG_DRV_Initial_PERI_CRG31_before_read_write_JPGD(HI_VOID){
        DRV_JPEG_OffClock();
        DRV_JPEG_OnClock();
        DRV_JPEG_Reset_PERI_CRG31_();
        msleep(3000);
        DRV_JPEG_CancelReset_PERI_CRG31_();
    }
    并把JPEG_DRV_Initial_PERI_CRG31_before_read_write_JPGD()函数放在初始化程序提前执行。示意如下：
    HI_S32 JPEG_DRV_ModInit(HI_VOID)
    {
        HI_S32 s32Ret = HI_FAILURE;
        #ifndef FIX_JPGD_REG_RW_CRASHED_BY_HUXM_20260728
    		JPEG_DRV_Initial_PERI_CRG31_before_read_write_JPGD();     // PERI_CRG31初始化要早于JPGD寄存器初始化。
        #endif
        #if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)
    	    hiJPEG_module_init();       // added by huxm 20260606   platform 平台解决硬件中断号到虚拟中断号转换
        #endif
    }
    

## 五、修复后信息输出：

    1、执行测试例程：
    	root@histb:~/sample/higo# ./sample_dec
    		 --- Get HDMI event: HOTPLUG. ---
    		HIGO Version            :4.0.0.0 SPC040 RELEASE
    		HIGO Build Time         :Sep  2 2016 15:47:47
    		HIGO Adp Version        :4.0.0.0 V1R2&V1R3&V1R5&V1R7 SPC040
    		HIGO Adp Build Time     :Sep  2 2016 15:47:49
    		press q to finish displaying
    		q
    	root@histb:~/sample/higo#
    	再也没有死机，测试程序正常显示所有图片。sample_effect、sample_performance、sample_stereo也通过了测试。
    2、查看hi_jpeg_irq中断号计数情况：
    	root@histb:~/sample/higo# cat /proc/interrupts | grep -E 'hi_vdp_irq|hi_tde_irq|hi_jpeg_irq'
    		 35:      67351       0          0          0     GIC-0 122 Level     hi_vdp_irq
    		 36:          0         39          0          0     GIC-0 123 Level     hi_tde_irq
    		 39:          0         77          0          0     GIC-0 129 Level     hi_jpeg_irq
    

## 六、修复方法的弊端

    1、弊端：
        从PMU（电源管理单元）角度看，在加载驱动时就给JPEG的硬件开启了时钟，而不是在使用JPEG硬件时，会增加整体的待机功耗。应该纠正
        一	点：这个不是驱动BUG的历史遗留问题，驱动正确的。只是higo算法库有一点点问题。但higo算法库没有开源源码，现在的修改最优解了。
    
    2、更优的修改方案：
    	不要在JPEG驱动里改，应该在higo算法库里改。同时在驱动里也要增加一个ioctl指令，在初始化JPGD寄存器前，单独开启PERI_CRG31的时
    	钟的ioctl指令。
    
    3、不能在测试例程改：
    	理由是在higo算库里，调用一个JPEG解码算法，包含了一系列open(),ioctl()的操作。你在例程里加这一系列操作，会与higo算法库里
    	JPEG解码算	法冲突。如果你在例程里不执行open()操作，ioctl操作系列是没有办法执行的。
    
    4、能不能修改JPEG_DRV_GetDevice()函数？
    	实测PERI_CRG31与JPGD寄存器操作之间，要有时间间隔。如果在JPEG_DRV_GetDevice()函数里改，higo算法库里JPEG解码算法可能是会
    	多次调用JPEG_DRV_GetDevice()函数，多次延时造成JPEG解码算法需要很长时间。在JPEG_DRV_GetDevice()函数有可能实现，要避免多
    	次延时造成JPEG解码算法慢。
    

## Support

若本文对你的学习与工作有所帮助、启发，欢迎支持！  
[SupportQR](../Support/SupportQR.md)

## 其它细节
