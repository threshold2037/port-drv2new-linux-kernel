## 背景介绍

        HiSTBLinuxV100R005C00SPC041B020版本的SDK是基于linux-3.18内核，比较旧。基于hi3798mv100硬件平台，
    把HiSTBLinuxV100R005C00SPC041B020版本的驱动移植到linux-5.15内核上。使用buildroot创建工具链，和根文件系统。
    全部代码的移植工作基本完成，编译通过。到了将代码放到目标硬件实际运行的阶段。
    

## 一、问题描述：

````shell
[   13.180091] Load hi_fb.ko success.           (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
[   13.673620] Mali: ERR: drivers/msp/gpu/mali4xx/common/mali_pp.c
[   13.679570]            mali_pp_create()  80
[   13.679570]
[   13.679583] Mali PP: Failed to setup interrupt handlers for PP core Mali_PP0
[   13.693239]
[   13.694734] Mali: ERR: drivers/msp/gpu/mali4xx/common/mali_kernel_core.c
[   13.701435]            mali_parse_product_info() 174
[   13.701435]
[   13.701442] Failed to create initial PP object
[   13.713267]
[   13.714852] Mali: ERR: drivers/msp/gpu/mali4xx/linux/mali_kernel_linux.c
[   13.721555]            mali_probe() 616
[   13.721555]
[   13.721562] mali_probe(): Failed to initialize Mali device driver.
[   13.727824]
[   13.735491] mali-utgard: probe of mali-utgard.0 failed with error -14
[   13.742028] Mali:
[   13.742033] Mali device driver loaded
[   13.764566] 8<--- cut here ---
[   13.767661] Unable to handle kernel paging request at virtual address fffb9ec5
[   13.774901] pgd = 2a3c235d
[   13.775824] 8<--- cut here ---
[   13.777624] [fffb9ec5] *pgd=26b34861, *pte=00000000, *ppte=00000000
[   13.780687] Unable to handle kernel paging request at virtual address 010605c0
[   13.780690]
[   13.780695] pgd = 2a3c235d
[   13.786955] Internal error: Oops: 37 [#1] SMP ARM
[   13.794167] [010605c0] *pgd=00000000
[   13.795640] Modules linked in: mali
[   13.798345]
[   13.803028]  hi_fb hi_mce hi_sync hi_aiao hi_adsp hi_cipher hi_vdec hi_vpss hi_svdec hi_vfmw hi_adec hi_demux hi_otp 
				hi_tde hi_i2c hi_gpio_i2c hi_gpio hi_vou hi_hdmi hi_pq hi_pdm hi_common hi_mmz hi_media
[   13.829771] CPU: 2 PID: 273 Comm: kworker/u8:4 Not tainted 5.15.134_s40 #32
[   13.836726] Hardware name: Hi3798MX-Platform
[   13.840988] Workqueue: rpciod rpc_async_schedule
[   13.845612] PC is at kmalloc+0x78/0x21c
[   13.849620] LR is at 0x81a43dc0
````

## 二、初步分析排查过程：

    1、找到出错的源文件：
    	根据错误信息用find ./source/msp/drv/ -type f -name "mali_pp.c"  
    		或  grep -nr "Failed to setup interrupt handlers for PP core"  ./source/msp/drv
    	
    2、定位到具体错误的程序片段：
    

````shell
	grep -nr -A2 -B13 "Failed to setup interrupt handlers for PP core"  mali_pp.c
	67-  core->irq = _mali_osk_irq_init(resource->irq,
	68-                                  mali_group_upper_half_pp,
	69-                                  group,
	70-                                  mali_pp_irq_probe_trigger,
	71-                                  mali_pp_irq_probe_ack,
	72-                                  core,
	73-                                  resource->description);
	74-  if (NULL != core->irq) {
	75-      mali_global_pp_cores[mali_global_num_pp_cores] = core;
	76-      mali_global_num_pp_cores++;
	77-
	78-      return core;
	79-  } else {
	80:MALI_PRINT_ERROR(("Mali PP: Failed to setup interrupt handlers for PP core %s\n", core->hw_core.description));
	81-  }
	82-  mali_group_remove_pp_core(group);
````

    3、分析：
    	程序中用_mali_osk_irq_init函数初始化，返回值给core->irq 赋值，core->irq=NULL。mail.ko的调用链：
    		mali_probe——→mali_initialize_subsystems——→mali_pp_create——→mali_osk_irq_init。 
    	但是Oops错误显示Unable to handle kernel paging request at virtual address fffb9ec5。并不是访问一个空指针导致Oops错误。
    	
    	再看另一个调用链：
    		rpc_async_schedule——→ rpc_execute——→ call_refresh——→ rpcauth_refreshcred——→ unx_lookup_cred——→ 
    		mempool_alloc——→ 	mempool_kmalloc——→ kmalloc。
    	kmalloc试图访问虚拟地址 fffb9ec5，这是一个非映射地址（*pgd=26b34861, 		*pte=00000000），导致 Unable to handle 
    	kernel paging request。
    	
    	core->irq=NULL是如何影响到另一个调用链，使得__kmalloc试图访问虚拟地址 fffb9ec5的呢？
    
    4、在.config中加入CONFIG_SLAB = y,在bootargs加入slub调试参数，重启。关键输出信息：
    

````shell
	             =============================================================================
	[   13.875786] BUG kmalloc-64 (Not tainted): Object already free
	[   13.881526] -----------------------------------------------------------------------------
					........................省略部分信息........................
	[   14.085011] Redzone  835257f0: bb bb bb bb bb bb bb bb bb bb bb bb bb bb bb bb  ................
	[   14.120111] Object   83525830: 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b a5  kkkkkkkkkkkkkkk.
	[   14.128886] Redzone  83525840: bb bb bb bb                                      ....
	[   14.136619] Padding  835258e8: 5a 5a 5a 5a 5a 5a 5a 5a 5a 5a 5a 5a 5a 5a 5a 5a  ZZZZZZZZZZZZZZZZ
	[   14.145394] Padding  835258f8: 5a 5a 5a 5a 5a 5a 5a 5a                          ZZZZZZZZ
					........................省略部分信息........................
	[   14.607315] =============================================================================
	[   14.615481] BUG kmalloc-64 (Tainted: G    B   ): Wrong object count. Counter is 17 but counted were 22
	[   14.625558] -----------------------------------------------------------------------------
	[   14.625558]
	[   14.635198] Slab 0xa6398480 objects=25 used=17 fp=0x83525580 flags=0x10201(locked|slab|head|zone=0)
	[   14.644239] CPU: 0 PID: 713 Comm: insmod Tainted: G    B             5.15.134_s40 #33
````

    这是典型是double free的bug。是发生错误后，同一块内存被释放了两次。
    
    总结：错误core->irq=NULL触发了，内存释放的操作，但是程序本身有BUG，重复内存释放导致的Oops错误。这里面可能包含两个错，一是
    	mali_osk_irq_init函数错误的根本原因，二是mali_osk_irq_init函数错误后，释放内存的过程中两次释放内存。
    

## 三、进一步精确定位：

    1、先解决Oops的严重问题。
    	我们先来解决第二个导致Oops的严重问题。根据错误信息的Backtrace信息：
    	第一次释放：`mali_pp_create`错误处理——→ `mali_group_remove_pp_core`——→ `_mali_osk_wq_delete_work`——→ `kfree`
    	第二次释放（触发 BUG）：`mali_initialize_subsystems`错误处理 ——→ `mali_terminate_subsystems`——→ `mali_group_delete`
    	——→ `_mali_osk_wq_delete_work`→ `kfree`
    
    2、定位到错误后释放内存程序片段：
    

````shell
	grep -A5 "mali_group_remove_pp_core"  mali_group.c
		void mali_group_remove_pp_core(struct mali_group *group)
		{
		        /* This group object no longer owns the PP core object */
		        group->pp_core = NULL;
		        if (NULL != group->bottom_half_work_pp) {
		                _mali_osk_wq_delete_work(group->bottom_half_work_pp);
		         }
		}
	
	grep -A46 'mali_group_delete' mali_group.c
		void mali_group_delete(struct mali_group *group)
		{
		        u32 i;
				....................................省略......................................
				if (NULL != group->bottom_half_work_pp) {
		                _mali_osk_wq_delete_work(group->bottom_half_work_pp);
		        }
		
		        _mali_osk_free(group);
		}
````

    3、根本原因判断：
    	从源码片段可以看到内存释放后，指针group->bottom_half_work_pp没有赋NULL值。
    4、修复办法：
    	两个函数加上group->bottom_half_work_pp = NULL;语句。问题解决。
    

## 四、修复源码

    略
    

## 五、问题解决后的信息输出：

````shell
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
````

    总结：输出信息中Mali模块中虽然有错误，但主要的Oops的错误已经解决。其它报错是程序中的常规报错。主要和core->irq=NULL有关。把这个问题作为另一个相关联独立问题来描述。
    

## Support

若本文对你的学习与工作有所帮助、启发，欢迎支持！  
[SupportQR](../Support/SupportQR.md)

## 其它细节
