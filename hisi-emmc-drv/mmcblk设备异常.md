## 背景介绍

         HiSTBLinuxV100R005C00SPC041B020版本的SDK是基于linux-3.18内核，比较旧。基于hi3798mv100硬件平台，
    把HiSTBLinuxV100R005C00SPC041B020版本的驱动移植到linux-5.15内核上。使用buildroot创建工具链，和根文件系统。
    全部代码的移植工作基本完成，编译通过。到了将代码放到目标硬件实际运行的阶段。
    

## 一、问题描述

    1、控制台输出：
    	[   34.066916] himciv200_wait_cmd_complete:625:
    	[   34.066973] himciv200_0: wait cmd request complete is timeout!Raw interrupt status 0x00000104, CMD5(0)
    	[   39.199126] himciv200_wait_cmd_complete:625:
    	[   39.199160] himciv200_0: wait cmd request complete is timeout!Raw interrupt status 0x00000104, CMD5(0)
    	[   44.331339] himciv200_wait_cmd_complete:625:
    	[   44.331368] himciv200_0: wait cmd request complete is timeout!Raw interrupt status 0x00000104, CMD5(0)
    	[   49.463553] himciv200_wait_cmd_complete:625:
    	[   49.463579] himciv200_0: wait cmd request complete is timeout!Raw interrupt status 0x00000104, CMD55(0)
    	[   54.595853] himciv200_wait_cmd_complete:625:
    	[   54.595879] himciv200_0: wait cmd request complete is timeout!Raw interrupt status 0x00000104, CMD55(0)
    	[   59.726981] himciv200_wait_cmd_complete:625:
    	[   59.727008] himciv200_0: wait cmd request complete is timeout!Raw interrupt status 0x00000104, CMD55(0)
    	[   64.859195] himciv200_wait_cmd_complete:625:
    	[   64.859229] himciv200_0: wait cmd request complete is timeout!Raw interrupt status 0x00000104, CMD55(0)
    	[   69.991408] himciv200_wait_cmd_complete:625:
    	[   69.991435] himciv200_0: wait cmd request complete is timeout!Raw interrupt status 0x00000104, CMD1(0)
    	[   75.635699] himciv200_wait_cmd_complete:625:
    	[   75.635726] himciv200_0: wait cmd request complete is timeout!Raw interrupt status 0x00000104, CMD52(C00)
    	[   80.767857] himciv200_wait_cmd_complete:625:
    	[   80.767883] himciv200_0: wait cmd request complete is timeout!Raw interrupt status 0x00000104, CMD52(80000C08)
    	[   85.901073] himciv200_wait_cmd_complete:625:
    	[   85.901101] himciv200_0: wait cmd request complete is timeout!Raw interrupt status 0x00000104, CMD0(0)
    	[   91.033283] himciv200_wait_cmd_complete:625:
    	[   91.033312] himciv200_0: wait cmd request complete is timeout!Raw interrupt status 0x00000104, CMD8(1AA)
    		周期性持续输出上面的信息。
    
    2、指令查看：
    		`root@histb:~# ls /dev/mmcblk*`
    			ls: cannot access '/dev/mmcblk*': No such file or directory
    		root@histb:~# ls /sys/bus/platform/devices/ | grep -i mmc
    			f9830000.himciv200.MMC
    		root@histb:~# ls /sys/class/mmc_host/
    			mmc0  mmc1
    

## 二、初步分析排查：

    1、初步判断：
    	从问题描述得到结论：platform 设备已经注册到总线， host 控制器存在，/dev没有mmcblk设备。是emmc枚举失败，控制台间隔5秒左
    	右的信息正是枚举的命令流系列。
    2、分析源码：
    	根据错误信息：himciv200_0: wait cmd request complete is timeout!Raw interrupt status 0x00000104...查找源码位置。
     grep -rn -C20 'wait cmd request complete is timeout' ./
    	./himciv200.c-661-static int himciv200_wait_cmd_complete(struct himciv200_host *host)
    	./himciv200.c-662-{               ......
    	./himciv200.c-670-    time = wait_event_timeout(host->intr_wait,
    	./himciv200.c-671-        test_bit(HIMCI_PEND_CD_b, &host->pending_events),time);
    	./himciv200.c-674-                 ......
    	./himciv200.c-675-    if ((time <= 0)&& (!test_bit(HIMCI_PEND_CD_b, &host->pending_events))) {
    	./himciv200.c-680-         regval = mci_readl(host, MCI_RINTSTS);
    	./himciv200.c:682:         himci_error("wait cmd request complete is timeout!"
    	./himciv200.c-683-        "Raw interrupt status 0x%08X, CMD%u(%X)\n", host->devid, regval, cmd->opcode, cmd->arg);
    	./himciv200.c-685-    }
    	./himciv200.c-699-                  ......
    	./himciv200.c-700-      return 0;
    	./himciv200.c-701-}
    从上面的程序可以分析出来，因为没有能等来HIMCI_PEND_CD_b置位，超时，打印出错误的信息。且读取原始中断状态寄存器regval = 
    mci_readl(host, MCI_RINTSTS)的值是0x00000104。
    3、源码增加打印信息：
    	1）、查看头文件himciv200_def.h得知0x00000104对应的是DTO_INT_STATUS和DRTO_INT_STATUS两个中断状态位。
    	
    	2）、根据himciv200_def.h提供的信息，在“2、”源码中增加MCI_MINTSTS、MCI_INTMASK、MCI_CTRL寄存器的打印信息。得到如下信息：
    	    MCI_RINTSTS=0x00000104,MCI_MINTSTS=0x00000004,MCI_INTMASK=0x0000040C,MCI_CTRL=0x02000010。
    	
    	3）、经过分析得知这几个寄存器对应的位是正确设置的。MCI_CTRL中EMMC host 中断总控制INTR_EN被 允许，和DMA中断
    	USE_INTERNAL_DMA被允许；MCI_INTMASK寄存器中的卡检测中断掩码CD_INT_MASK、数据传输超时中断掩码DTO_INT_MASK、电压切换中断
    	掩码VOLT_SWITCH_INT_MASK被置位，它们对应的中断被允许；MCI_MINTSTS寄存器则指示数据传输超时中断状态DTO_INT_STATUS发生；
    	 MCI_MINTSTS寄存器比MCI_RINTSTS寄存器少了DRTO_INT_STATUS状态位，应该是对应的MCI_INTMASK寄存器中对应的位被屏蔽了。
    	
    	4）、最终的结论是，寄存器设置正常，发生了数据传输超时中断，但是在中断里可能没有对类似于HIMCI_PEND_CD_b的位
    	HIMCI_PEND_DTO_b和HIMCI_PEND_CD_b本身置位，或是中断服务程序根本没有被执行。
    
    4、中断分析：
    	1）、在中断服务程序himciv200_irq()中开头位置加入打印信息，没有信息输出。中断服务程序根本没有被执行。
    	
    	2）、cat /proc/interrupts | grep himciv200
    		 26:     0      0      0      0     GIC-0  67 Edge      himciv200       也证实中断服务程序确实没有被执行。
    
    	3）、cat /sys/kernel/debug/clk/clk_summary | grep CLKS_CTRL_CRG40_SDIO1
    		 CLKS_CTRL_CRG40_SDIO1         2       2       0   100000000        0     0  50000       Y	 
    

《[时钟控制器驱动问题](../hisi-clk-drv/%E6%97%B6%E9%92%9F%E6%8E%A7%E5%88%B6%E5%99%A8%E9%A9%B1%E5%8A%A8%E9%97%AE%E9%A2%98.md)》一文中也证实时钟是正常的。

     4）、probe()函数中ret = request_irq(host->irq, himciv200_irq, 0, DRVNAME, host);语句前后增加打印信息，证实注册成功。
     
     5）、检查设备树配置中，中断号与手册信息相符。“2）、”和设备树显示中断触发类型是边沿触发。但是根据
    

《[gpu的中断号问题](../hisi-gpu-drv/gpu%E7%9A%84%E4%B8%AD%E6%96%AD%E5%8F%B7%E9%97%AE%E9%A2%98.md)》一文中 的经验，中断触发类型一般情况是高电平触发。

     6）、查看HiSTBLinuxV100R005C00SPC041B020版本DTS文件：grep -A10 'himciv200.MMC@0xf9830000' ./hi3798mv100.dts
                himciv200.MMC@0xf9830000 {
                        compatible = "hi3798mv100,himciv200";
                        reg = <0xf9830000 0x1000>;
                        interrupts = <0 35 4>;
                        .......
                };
        确实是移植时弄错了，interrupts = <0 35 4>，4应该是高电平触发。
    
    5、中断风暴：
    	1）、设备树配置中，把中断触发类型改成高电平触发，立即触发中断风暴。耗尽CPU处理能力，死机。
    	
    	2）、中断服务程序中打印MCI_MINTSTS、MCI_RINTSTS、MCI_CDETECT寄存器。清除MCI_MINTSTS寄存器防止反复中断，查看卡检测的状
    	态有没有MCI_CDETECT出现不稳定现象。输出信息如下：
    		[   22.650861] himciv200 irq 1561 times,MCI_MINTSTS=0x00000000,MCI_RINTSTS=0x00000000,MCI_CDETECT=0x00000000,
    	
    	3）、瞬时发生了1561次中断，MCI_MINTSTS和MCI_RINTSTS显示没有发生中断，MCI_CDETECT检测稳定输出0值，没有其它跳变的值。
    	原来的超时错误再也没有发生，中断风暴耗尽CPU。
    	
    	4）、奇怪的事发生了，MCI_MINTSTS和MCI_RINTSTS显示没有发生中断，事实却是短时间内打印了1561条信息，发生了中断风暴。分析进入了
    		死胡同。
    

## 三、深入分析原因

    1、其它中断：
    	MCI_MINTSTS和MCI_RINTSTS显示没有发生中断，还有其它中断。根据MCI_CTRL寄存器中EMMC host 中断总控制INTR_EN被允许外，还有
    	DMA中断USE_INTERNAL_DMA被允许；查看头文件himciv200_def.h，与DMA相关的内容。
    2、DMA中断：
    	中断服务程序增加打印DMA中断，输出信息如下：
    		[    4.092118] himciv200 irq 32 times,MCI_MINTSTS=0x00000000,MCI_RINTSTS=0x00000000,MCI_IDSTS=0x00000102
    		MCI_IDSTS寄存器（应该是Internal DMA Status缩写）不是0，证实确实是发生了DMA相关的中断风暴。
    3、区分中断风暴：
    	区分是持继产生DMA中断事件，还是中断状态位没有清除产生的中断风暴。在中断服务程序中清除MCI_IDSTS寄存器。再也没有发生中断暴。
    	成功解决问题。
    4、真正的原因：
    	查看HiSTBLinuxV100R005C00SPC041B020版本的中断服务程序，是一模一样的。为什么在linux-3.18内核中却没有发生中断风暴。可能
    	合理的推测是：Linux 5.15 的 MMC 核心层通过以下机制导致 IDMAC 中断在实际运行中被使能：
    	- MMC host capability 标志的默认值变化
    	- 内核 DMA 子系统（DMA Engine、IOMMU）的行为变化
    	而 3.18 的 MMC 核心层环境下，host 驱动运行后 MCI_IDINTEN 的 IDMAC 位实际为 0，所以 bug 被掩盖。
    

## 四、修复源码

    略
    

## 五、问题解决后的信息输出：

    1、启动日志信息：
    	[    4.611900] mmc0: new DDR MMC card at address 0001
    	[    4.639264] mmcblk0: mmc0:0001 P1XXXX 3.57 GiB
    	[    4.768755] mmcblk0boot0: mmc0:0001 P1XXXX 2.00 MiB
    	[    4.840555] mmcblk0boot1: mmc0:0001 P1XXXX 2.00 MiB
    	[    4.892866] mmcblk0rpmb: mmc0:0001 P1XXXX 128 KiB, chardev (250:0)
    	EMMC 正确枚举。
    2、中断统计信息：
    	cat /proc/interrupts | grep himciv200
    	 26:        196          0          0          0     GIC-0  67 Level     himciv200
    

## Support

若本文对你的学习与工作有所帮助、启发，欢迎支持！  
[SupportQR](../Support/SupportQR.md)

## 其它细节
