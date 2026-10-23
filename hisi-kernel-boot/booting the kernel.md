## 背景介绍

        HiSTBLinuxV100R005C00SPC041B020版本的SDK是基于linux-3.18内核，比较旧。基于hi3798mv100硬件平台，
    把HiSTBLinuxV100R005C00SPC041B020版本的驱动移植到linux-5.15内核上。使用buildroot创建工具链，和根文件系统。
    全部代码的移植工作基本完成，编译通过。到了将代码放到目标硬件实际运行的阶段。
    

## 一、问题描述

    Bootrom start
    Boot from eMMC
    Starting fastboot ...
    	.......................省略uboot启动信息.......................
    Booting kernel from Legacy Image at 01ffffc0 ...
       Image Name:   Linux-5.15.134_s40
       Image Type:   ARM Linux Kernel Image (uncompressed)
       Data Size:    9203935 Bytes = 8.8 MiB
       Load Address: 02000000
       Entry Point:  02000000
       Verifying Checksum ... OK
       XIP Kernel Image ... OK
    OK
    
    Starting kernel ...
    
    Uncompressing Linux... done, booting the kernel.
    静默挂起，再也没有信息输出。
    

## 二、初步分析排查：

    1、初步判断：
    	属于典型的内核早期初始化阶段静默崩溃。
    2、初步分析：
    	1）、从信息上看，u-boot正确识别了zImage的头部信息，ATAGS信息，zImage校验码正确。开始解压，解压完成。开始由u-boot运行到
    	内核运行的阶段。
    	2）、我们不去分析内核的启动原理，比如，MMU还没有设置下的地址对齐，设置页表，解压时如何计算解压后的执行地址有没有覆盖
    	堆栈、DTB、zImage、_edata、.bss段等。
    	3）、我们只分析在哪个点加入打印信息，跟踪程序执行到哪静默挂起。只从实际操作层面去分析。
    3、查看最后信息源码：
    		 grep -rn  'Uncompressing Linux...' .
    			./boot/compressed/misc.c:155:   putstr("Uncompressing Linux...");
    		sed -n '141,144p;155,163p' ./boot/compressed/misc.c
    			void	decompress_kernel(unsigned long output_start, unsigned long free_mem_ptr_p,
    			                unsigned long free_mem_ptr_end_p,
    			                int arch_id)
    			        putstr("Uncompressing Linux...");
    			        ret = do_decompress(input_data, input_data_end - input_data,
    			                            output_data, error);
    			        if (ret)
    			                error("decompressor returned an error");
    			        else
    			                putstr(" done, booting the kernel.\n");
    			
    			}
    	在函数decompress_kernel中执行解压内核的do_decompress函数，成功执行了‘putstr(" done, booting the kernel.\n");’语句。
    
    4、增加打印信息：
    	1）、arch/arm/boot/compressed/head.S执行阶段：
    		不要指望在这个阶段有printk或early_print，只能用puts,phex打印字符和数字，memdump打印寄存器的值。找到这个程序的
    		入口start，不建议在 `start:` 入口直接插入打印指令，因为入口区域的填充指令承担着兼容性职责。找到
    		“bl  decompress_kernel”语句之后的，	“bl  cache_clean_flush”、“bl  __hyp_set_vectors”语句的后面，
    		“b   __enter_kernel”的前面加打印信息。	“bl  decompress_kernel”之前的	“bl  __hyp_stub_install”、	
    		“bl  fdt_check_mem_start”、“bl  atags_to_fdt”、“bl  cache_clean_flush”这几个点被证明是正常的。
    	结果都有信息输出。不是在arch/arm/boot/compressed/head.S阶段静默挂起。
    	
    	2）、arch/arm/kernel/head.S执行阶段：
    		arch/arm/boot/compressed/head.S文件中执行“b   __enter_kernel”就到了arch/arm/kernel/head.S的ENTRY(stext)入口。
    		在相同目录，即arch/arm/kernel目录还有一个debug.S文件。里面定义了printascii函数，使用它分别在
    		“bl  __lookup_processor_type”的前一语句、“bl  __vet_atags”、“bl  __create_page_tables”的后面，
    		“b   __enable_mmu”、“b   __turn_mmu_on”的前面都加上打印信息。在执行“b   __enable_mmu”，会设置一
    		个“__mmap_switched”、中断地址，“b   __turn_mmu_on”执行之后，会产生中断，转到“__mmap_switched”地址。
    	结果都有信息输出。
    	
    	3）、arch/arm/kernel/head-common.S执行阶段：
    		这个文件里有个中断入口“__mmap_switched”地址，在“bl  __inflate_kernel_data”、“bl  __memcpy”、
    		“bl  __memset”的后面，“b start_kernel”的前面都加上打印信息。
    	结果都有信息输出。
    	
    	4）、init/main.c执行阶段：
    		“b start_kernel”执行就跳转到init/main.c文件里的start_kernel函数了。这里就全部是C语言的程序了。start_kernel函数
    		的开始，
    		printk函数还不能打印信息，但是也不会在编译阶段报错。printascii函数在这里编译不报错，但在链接时报错。
    

## 三、进一步精确定位：

    1、继续查找线索：
    	grep -r 'printascii' .
    								.......
    		./kernel/early_printk.c:                printascii(buf);
    								.......
    		./kernel/setup.c:       printascii(buf);
    								.......
    		./Kconfig.debug:          Say Y here to include definitions of printascii, printch, printhex
    								.......
    	对3个有可能封装printascii函数，在C语言中继续使用的文件，查看、分析它。./kernel/early_printk.c确实是对printascii函数封装，
    	但在start_kernel函数入口不具备注册它，使用它的条件。
    
    2、关键发现：
    	grep -r -C4 'printascii' ./kernel/setup.c
    		void early_print(const char *str, ...)
    		{
    		        extern void printascii(const char *);
    		        char buf[256];
    		        va_list ap;
    		        va_start(ap, str);
    		        vsnprintf(buf, sizeof(buf), str, ap);
    		        va_end(ap);
    		#ifdef CONFIG_DEBUG_LL
    		        printascii(buf);
    		#endif
    		        printk("%s", buf);
    		}
    	打开选项CONFIG_DEBUG_LL，函数early_print就是调用printascii的。./Kconfig.debug里的帮助信息“ Say Y here to include 
    	definitions of printascii, printch, printhex in the kernel.”也相互印证了。
    
    3、打开CONFIG_DEBUG_LL选项：
    	打开CONFIG_DEBUG_LL选项，给start_kernel函数每个函数调用都加上打印信息，重新编译，加载运行，输出信息如下：
    		ATAGS [0x00000100 - 0x000002B0], 432Bytes
    		Starting kernel ...
    		Uncompressing Linux... done, booting the kernel.
    		DEBUG: Reached start_kernel FIRST LINE
    						.......
    		DEBUG: before setup_arch(&command_line);
    		Error: invalid dtb and unrecognized/unsupported machine ID
    		  r1=0x00001f40, r2=0x00000100
    		  r2[]=05 00 00 00 01 00 41 54 00 00 00 00 00 00 00 00
    		Available machine support:
    		ID (hex)        NAME
    		ffffffff        Hi3798MX-Platform
    		Please check your kernel config and/or bootloader.
    	信息显示data abort的地方在start_kernel函数的setup_arch函数。无效的DTB 和无法识别/不支持的机器ID。ARM Linux 启动约定，
    	r1=0x00001f40，bootloader 传入的 machine ID。换算十进制是 8000，这个 ID 在内核中找不到匹配项。r2 寄存器传的是ATAGS地址
    	或DTB地址，现在用的较老u-boot，传的是ATAGS地址.
    

## 四、修复方法：

    1、加上machine ID:
    	arm/tools/mach-types文件末尾补上machine ID。
    
    2、输出信息：
    	ATAGS [0x00000100 - 0x000002B0], 432Bytes
    	Starting kernel ...
    	Uncompressing Linux... done, booting the kernel.
    	DEBUG: Reached start_kernel FIRST LINE 
    	没有出错信息了，但是data abort了。原来报错的原因是，u-boot传入的r2=0x100指向ATAGS，其头部magic并非FDT的`0xd00dfeed`，
    	`setup_machine_fdt`解析失败后回退到machine ID查找，而`DT_MACHINE_START`注册的`nr=~0`与传入的8000无法匹配，因此打印
    	了Error。补上machine ID后，报错消失，原因是内核仍将r2当作DTB解析。ATAGS既非合法FDT，又无DTB模板可用，内核访问非法内存触发
    	异常，而控制台尚未初始化，所以静默。单独补machine ID只是消除报错，无法真正启动。
    
    3、回顾：
    	再考虑Error: invalid dtb；u-boot传入的machine ID是8000，Available machine support:ID (hex)ffffffff。永远也不可能
    	匹配！！
    		grep -rwn -A5 '#define DT_MACHINE_START' .
    			./include/asm/mach/arch.h:91:#define DT_MACHINE_START(_name, _namestr)          \
    			./include/asm/mach/arch.h-92-static const struct machine_desc __mach_desc_##_name       \
    			./include/asm/mach/arch.h-93- __used                                                    \
    			./include/asm/mach/arch.h-94- __section(".arch.info.init") = {                  \
    			./include/asm/mach/arch.h-95-   .nr             = ~0,                           \
    			./include/asm/mach/arch.h-96-   .name           = _namestr,
    		.nr             = ~0,就是0xffffffff。
    	看来是比较新的内核是不支持这种方式的。只能使用DTB方式。
    
    4、查看.config:
    		 grep 'CONFIG.*DTB.*' ./arm/configs/hi3798mv100_defconfig
    				......
    			# CONFIG_ARM_APPENDED_DTB is not set
    	原因可能就在# CONFIG_ARM_APPENDED_DTB is not set，把它改成CONFIG_ARM_APPENDED_DTB = y。还要加上
    	CONFIG_ARM_ATAG_DTB_COMPAT=y。原因是：这个 u-boot 通过 ATAGS 传递参数，而不是直接传递 DTB 地址。内核镜像仍然是老的 
    	uImage 格式，也就是说 DTB 块是附加在 zImage 末尾的。因此，必须开启 `CONFIG_ARM_ATAG_DTB_COMPAT`，让内核能够将 u-boot 传
    	入的 ATAGS 信息	（启动参数、如内存布局、Initrd 地址等）转换成 FDT 格式，动态转换成设备树二进制文件（DTB）中的属性。从而让使
    	用旧版 U-Boot的设备也能启动仅支持设备树（DTB）的新内核。 
    
    5、正常启动。
    

## 五、效果演示

    	Starting kernel ...
    	Uncompressing Linux... done, booting the kernel.
    	hi3798mx_map_io         [arch/arm/mach-hi3798mx/core.c]
    	[    0.000000] Booting Linux on physical CPU 0x0
    	[    0.000000] Linux version 5.15.134_s40 (u2204@u2204) 
    		(arm-hisi-linux-gnueabi-gcc.br_real (Buildroot -gbfb24b47) 
    		12.3.0, GNU ld (GNU Binutils) 2.40) #394 SMP Sat Aug 29 23:26:58 CST 2026
    

## Support

若本文对你的学习与工作有所帮助、启发，欢迎支持！  
[SupportQR](../Support/SupportQR.md)

## 其它细节
