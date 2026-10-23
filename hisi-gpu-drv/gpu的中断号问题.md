## 背景介绍

        HiSTBLinuxV100R005C00SPC041B020版本的SDK是基于linux-3.18内核，比较旧。基于hi3798mv100硬件平台，
    把HiSTBLinuxV100R005C00SPC041B020版本的驱动移植到linux-5.15内核上。使用buildroot创建工具链，和根文件系统。
    全部代码的移植工作基本完成，编译通过。到了将代码放到目标硬件实际运行的阶段。
    

## 一、问题描述：

    [   14.191020] Mali: ERR: drivers/msp/gpu/mali4xx/common/mali_pp.c
    [   14.196992]            mali_pp_create()  80
    [   14.196992]
    [   14.197001] Mali PP: Failed to setup interrupt handlers for PP core Mali_PP0
    [   14.210662]
    [   14.212172] Mali: ERR: drivers/msp/gpu/mali4xx/common/mali_kernel_core.c
    [   14.218877]            mali_parse_product_info() 174
    [   14.218877]
    [   14.218884] Failed to create initial PP object
    [   14.230727]
    [   14.238574] Mali: ERR: drivers/msp/gpu/mali4xx/linux/mali_kernel_linux.c
    [   14.245320]            mali_probe() 616
    [   14.245320]
    [   14.245329] mali_probe(): Failed to initialize Mali device driver.
    [   14.251607]
    [   14.259287] mali-utgard: probe of mali-utgard.0 failed with error -14
    [   14.265993] Mali:
    [   14.266002] Mali device driver loaded
    

## 二、初步分析排查：

请参考《[gpu的oops问题 > 二、初步分析排查过程：](gpu%E7%9A%84oops%E9%97%AE%E9%A2%98.md#er-chu-bu-fen-xi-pai-cha-guo-cheng)》

## 三、进一步精确定位：

1、在 《[gpu的oops问题](gpu%E7%9A%84oops%E9%97%AE%E9%A2%98.md)》中，已经解决第二个问题，现在我们来解决第一个问题，即core->irq=NULL。进一步找到
mali_osk_irq_init函数的定义：

    grep "_mali_osk_irq_init" mali_osk_irq.c
    _mali_osk_irq_t *_mali_osk_irq_init(u32 irqnum, _mali_osk_irq_uhandler_t uhandler, void *int_data, 
     _mali_osk_irq_trigger_t trigger_func, _mali_osk_irq_ack_t ack_func, void *probe_data, const char *description)
    
    函数的形参分别是“中断号”，“中断处理函数指针”，“给 `uhandler`的自定义数据指针”，“中断触发配置函数指针”，“中断确认函数指针”，“探测
    阶段传入的附加数据”，“探测阶段传入的附加数据”。返回值是中断号。
    
    如果是新写的程序，只能对_mali_osk_irq_init函数的内容全部检查和调试，重点查看它返回NULL的段。现在是驱动程序移值。背景是驱动程序在
    3.18内核是正常工作的，移值到5.15内核出现错误。查阅官方文档，5.15内核对中断号是有更严格的要求的。3.18内核是可以直接用芯片的硬件中
    断号直接注册的。5.15内核是禁止的，只能使用设备树，platform映射一个虚拟中断号再用request_irq申请注册中断号。
    

2、查看_mali_osk_irq_init的关键内容：

````shell
	sed -n '110p;112p;119,129p;133p;141p' mali_osk_irq.c
		if (-1 == irqnum) {
				if ((NULL != trigger_func) && (NULL != ack_func)) {
					do {
							unsigned long mask;
							mask = probe_irq_on();
							trigger_func(probe_data);
							_mali_osk_time_ubusydelay(5);
							irq = probe_irq_off(mask);
							err = ack_func(probe_data);
					while (irq < 0 && (err == _MALI_OSK_ERR_OK) && probe_count--);
				} else irqnum = -1; /* no probe functions, fault */
		}
````

     这段程序最后兜底的设计，如果传给_mali_osk_irq_init函数的IRQ号是错，通过内核函数probe_irq_on();和probe_irq_off(mask);获得正确
    的IRQ号。这段程序也没有起到作用。这里涉及到硬件调试，不去钻牛角尖，先从比较简单的给_mali_osk_irq_init函数传入正确的IRQ号入手解决
    问题。后续需要再来查清楚这段程序为什么没有起作用。
    

3、在_mali_osk_irq_init函数被调用的代码片段：

````shell
	grep -nr -A2 -B13 "Failed to setup interrupt handlers for PP core"  mali_pp.c
	67-  core->irq = _mali_osk_irq_init(resource->irq,
	68-                                 mali_group_upper_half_pp,
	69-                                 group,
	70-                                 mali_pp_irq_probe_trigger,
	71-                                 mali_pp_irq_probe_ack,
	72-                                 core,
	73-                                 resource->description);
	74-  if (NULL != core->irq) {
	75-      mali_global_pp_cores[mali_global_num_pp_cores] = core;
	76-      mali_global_num_pp_cores++;
	77-
	78-      return core;
	79-  } else {
	80: MALI_PRINT_ERROR(("Mali PP: Failed to setup interrupt handlers for PP core %s\n", core->hw_core.description));
	81-  }
	82-  mali_group_remove_pp_core(group);
````

    排查resource->irq 传入的错误值是更简单的解决办法。
    
    mail.ko的调用链：mali_probe——→mali_initialize_subsystems——→mali_pp_create()———→mali_osk_irq_init。
    
    细看所有调用mali_pp_create的详细的上下文，有一个_mali_osk_resource_find函数。
    

````shell
	grep -r "_mali_osk_resource_find" ./msp/drv/gpu
		linux/mali_osk_mali.h:_mali_osk_errcode_t _mali_osk_resource_find(u32 addr, _mali_osk_resource_t *res);       
		common/mali_kernel_core.c: resource_pp_found[0] = _mali_osk_resource_find(MALI_OFFSET_PP0, &(resource_pp[0]));
````

    看_mali_osk_resource_find函数第一个函数参数是地址。多处调用_mali_osk_resource_find，MALI_OFFSET_PP0就是地址宏。
    

````shell
grep -r "MALI_OFFSET_PP0" ./msp/drv/gpu
		mali/mali_utgard.h:#define MALI_OFFSET_PP0                   0x08000     证实是址址。
````

    打开mali_utgard.h查看详细的内容，发现了:
    	"#define MALI_GPU_RESOURCES_MALI450_MP4_PMU(base_addr,gp_irq,...)     ...."
    

````shell
grep -r "MALI_GPU_RESOURCES_MALI450_MP4_PMU" ./msp/drv/gpu
		arm/arm.c: MALI_GPU_RESOURCES_MALI450_MP4_PMU(0xFC040000, -1, 70, 70, 70, 70, 70, 70, 70, 70, 70, 68);
````

     至此，找到中断号赋值处，有两个主要的硬件中断号70和68。
    

4、修复程序设想：

     在设备树里加入辅助gpu节点，写hiGPU_AUX_irq_auto_probe()函数，使用platform_get_irq()得到由硬件中断号到软件中断号的转换。在mali_probe()函数调用mali_initialize_subsystems()函数之前，用虚拟中断号覆盖原来定义的硬件中断号。
    

## 四、修复源码

略

## 五、修复后信息输出：

    [   14.026396] hiGPU_AUX_irq_auto_get soc:amba:hi3798mv100.hiGPU_AUX: Mali IRQs: 126->42, 70->43, 68->34
    [   14.046731] Load mali.ko success.    (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    
    总结：用这种方法较好的解决从3.18内核移值驱动到5.15内核，关于原驱动直接用硬件中断号注册的问题。并且这种方式，对原来的源代码改动很少，不会引入新的BUG。增加的源码是可以模块化的。只在1处或2或调用增加的函数即可。
    

## Support

若本文对你的学习与工作有所帮助、启发，欢迎支持！  
[SupportQR](../Support/SupportQR.md)

## 其它细节
