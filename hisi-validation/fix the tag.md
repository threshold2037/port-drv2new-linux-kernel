
    grep -r -E 'huxm 2023|HUXM_2023' ./
    	./kernel/linux-5.15.134/Makefile:# modify by huxm 20231215
    	./kernel/linux-5.15.134/Makefile:#Added Kernel515 Kernel318 option Modify by huxm 20231216
    	./kernel/linux-5.15.134/Makefile:#Added by huxm 20231216
    	./kernel/linux-5.15.134/Makefile:# modify by huxm 20231216 Add user supplied CPPFLAGS, AFLAGS 
    											and CFLAGS as the last assignments
    	./kernel/linux-5.15.134/arch/arm/Makefile:#added ARCH_HI3798MX by huxm 20231216
    	./kernel/linux-5.15.134/arch/arm/boot/Makefile:#added $(srctree)/ before $(MACHINE) by huxm 20231226
    	./kernel/linux-5.15.134/arch/arm/boot/Makefile:#added by huxm 20231226
    	./kernel/linux-5.15.134/arch/arm/boot/Makefile:#added targets "zImage-dtb" by huxm 20231226
    	./kernel/linux-5.15.134/arch/arm/boot/Makefile:#added by huxm 20231226
    	./kernel/linux-5.15.134/arch/arm/boot/Makefile:#added by huxm 20231226
    	./kernel/linux-5.15.134/arch/arm/boot/Makefile:# changed "zImage" to "zImage-dtb" by huxm 20231226
    	./kernel/linux-5.15.134/arch/arm/boot/Makefile:# added by huxm 20231226
    	./kernel/linux-5.15.134/arch/arm/boot/dts/Makefile:#added by huxm 20231226
    	./kernel/linux-5.15.134/arch/arm/Kconfig:#added by huxm 20231214
    	./kernel/linux-5.15.134/arch/arm/Kconfig:#added by huxm 20231215
    	./kernel/linux-5.15.134/arch/arm/Kconfig:#added by huxm 20231214
    	./kernel/linux-5.15.134/arch/arm/mach-hi3798mx/platsmp.c:int pen_release;               //added by huxm 20231216
    	./kernel/linux-5.15.134/arch/arm/mach-hi3798mx/platsmp.c:
    								static void  write_pen_release(int val)                //modify by huxm 20231216
    	./kernel/linux-5.15.134/arch/arm/mach-hi3798mx/platsmp.c: struct task_struct *idle)     //modify by huxm 20231216
    	./kernel/linux-5.15.134/arch/arm/mach-hi3798mx/platsmp.c:static 
    								void hi3798mx_secondary_init(unsigned int cpu)          //modify by huxm 20231216
    	./kernel/linux-5.15.134/arch/arm/mach-hi3798mx/hotplug.c:extern int pen_release;        //added by huxm 20231216
    	./kernel/linux-5.15.134/arch/arm/mach-hi3798mx/headsmp.S://     __CPUINIT               //modify by huxm 20231216
    	./kernel/linux-5.15.134/arch/arm/mach-hi3798mx/headsmp.S:
    													/* modify end    modify by huxm 20231216             */
    	./kernel/linux-5.15.134/include/linux/clockchips.h:     // added by huxm 20231218
    	./kernel/linux-5.15.134/drivers/Makefile:#added by huxm 20231214
    	./kernel/linux-5.15.134/drivers/mtd/Kconfig:#added by huxm 20231219
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/hrtimer_test.c:// added by huxm 20230109
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/hrtimer_test.c:// added by huxm 20230109
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:
    							/* ------------------------- added by huxm 20231218  -------------------------- */
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:
    							/* ---------------------end of added by huxm 20231218  ------------------------ */
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:  
    						clksrc->read   = &hisi_clocksource_read;                // added (u64)(& ) by huxm 20231218
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hiir.c:
    										#include "../clk-hisi.h"              // added "../"by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hiir.c:
    										#include <asm-generic/io.h>           // added "../"by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hiir.c:              // added by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hiusb3.c:
    												#include "../clk-hisi.h"    // added "../"by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hiusb3.c:
    												#include "asm-generic/io.h"   // added "../"by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:
    													#include <linux/version.h>   // added by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:
    										#include "../clk-hisi.h"               // added "../"by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:
    											#include "asm-generic/io.h"            // added by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hiusb2.c:                    by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hiusb2.c:
    												#include "../clk-hisi.h"      // added "../"by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hiusb2.c:
    						#include "asm-generic/io.h"                                 // added "../"by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.h:#include <linux/version.h>   // added by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.c:
    						#include "asm-generic/io.h"                                    // added by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.c:               
    												init.flags = 0;                 // added by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/misckernel4/hifixtimer.c:
    								extern int setup_irq(int,struct irqaction *);        // added by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/misckernel4/hifixtimer.c:     //modify by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/misckernel4/part-change.c:
    				static const struct proc_ops cmdline_parts_fops = {         // modify const struct by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/misckernel4/part-change.c:    
    		entry = proc_create("partchange", 0755, NULL, &(cmdline_parts_fops));// added (const struct) by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/misckernel4/export_sym.c:
    										EXPORT_SYMBOL(irq_set_affinity);     // modify by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/soc/hi3798mv100/hipm.c:// added by huxm 20231219
    	./kernel/linux-5.15.134/drivers/hisilicon/soc/hi3798mv100/hipm_sleep.S:/*       instruction end by huxm 20231217*/
    	./kernel/linux-5.15.134/drivers/hisilicon/kapi/pdm.c:   
    									atomic_long_add(pages, &_totalram_pages);       // modify by huxm 20231216
    	./kernel/linux-5.15.134/drivers/hisilicon/misc/hw_breakpoint.c:
    									#include <uapi/linux/sched/types.h>              // added by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/misc/hw_breakpoint.c:// added by huxm 20231219
    	./kernel/linux-5.15.134/drivers/hisilicon/misc/hw_breakpoint.c:
    									extern int show_regs(struct pt_regs *);          // added by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/misc/hw_breakpoint.c: 
    			//struct sched_param param = { .sched_priority = MAX_RT_PRIO - 1 };           // comment huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/misc/hw_breakpoint.c: 
    		static const struct sched_param param = {.sched_priority = MAX_RT_PRIO-1};//added "static const" huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/misc/part-change.c:
    												//#include <linux/cmdline-parser.h> // delete by huxm 20231220
    	./kernel/linux-5.15.134/drivers/hisilicon/misc/part-change.c:// added by huxm 20231220
    	./kernel/linux-5.15.134/drivers/hisilicon/misc/part-change.c:
    										/*=======  added mtd_part_change() by huxm 20231220 ==========*/
    	./kernel/linux-5.15.134/drivers/hisilicon/misc/part-change.c:/* delete by huxm 20231220
    	./kernel/linux-5.15.134/drivers/hisilicon/misc/part-change.c:added by huxm 20231220             */
    	./kernel/linux-5.15.134/drivers/hisilicon/misc/part-change.c:   // added (struct proc_ops *) by huxm 20231220
    	./kernel/linux-5.15.134/drivers/hisilicon/misc/export_sym.c:
    									//EXPORT_SYMBOL(__irq_set_affinity);        // delete by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/misc/export_sym.c:
    									//extern struct list_head gpio_chips;       // delete by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/misc/export_sym.c:
    										extern struct list_head gpio_devices;       // added by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/misc/export_sym.c:
    								//EXPORT_SYMBOL(gpio_chips);                        // delete by huxm 20231217
    	./kernel/linux-5.15.134/drivers/hisilicon/misc/export_sym.c:
    								EXPORT_SYMBOL(gpio_devices);                        // added by huxm 20231217
    	./kernel/linux-5.15.134/block/partitions/cmdline.c:#include <linux/cmdline.h>   // added by huxm 20231218
    	./kernel/linux-5.15.134/block/partitions/cmdline.c:#if 0                        // delete by huxm 20231218
    	./kernel/linux-5.15.134/block/partitions/cmdline.c:
    				void cmdline_parts_free(struct cmdline_parts **parts)        // delete "static"by huxm 20231218
    	./kernel/linux-5.15.134/block/partitions/cmdline.c:
    								// const char *cmdline)                   // delete "static"by huxm 20231218
    	./kernel/linux-5.15.134/block/partitions/cmdline.c:
    								// struct parsed_partitions *state)       // delete "static"by huxm 20231218
    	./kernel/linux-5.15.134/block/partitions/cmdline.c:
    					//static int __init cmdline_parts_setup(char *s)     // delete "static"by huxm 20231218
    	./kernel/linux-5.15.134/scripts/Makefile.lib:# delete by huxm 20231226
    	./kernel/linux-5.15.134/scripts/Makefile.lib:#added by huxm 20231226
    
    grep -r -E 'huxm 2024|HUXM_2024' ./
    	./msp/drv/cipher/drv_cipher_intf.c:    #if 0       // added by huxm 20241210
    	./msp/drv/pdm/drv_pdm.c://#include <linux/bootmem.h>        // delect by huxm 20241208
    	./msp/drv/pvr/drv_pvr_intf.c:    #if 0       // added by huxm 20241210
    	./msp/drv/pq/pq_v4_0/drv_pq_intf.c:    #if 0       // added by huxm 20241210
    	./msp/drv/pq/pq_v3_0/drv_pq_intf.c:    #if 0       // modify by huxm 20241208
    	./msp/drv/venc/venc_v2.0/drv_venc_intf.c:    #if 0       // added by huxm 20241210
    	./msp/drv/venc/venc_v1.0/drv_venc.c:// added by huxm 20241216
    	./msp/drv/venc/venc_v1.0/drv_venc.c:        #if 0                       // delete by huxm 20241218
    	./msp/drv/venc/venc_v1.0/drv_venc.c:        #else                       // added by huxm 20241218
    	./msp/drv/venc/venc_v1.0/drv_venc.c:        
    							vencTimer.function = (void *)VENC_TimerFunc;    // added (void *) by huxm 20241216
    	./msp/drv/venc/venc_v1.0/drv_venc_intf.c:        #if 0                  // delete by huxm 20241218
    	./msp/drv/venc/venc_v1.0/drv_venc_intf.c:           #else                       // added  by huxm 20241218
    	./msp/drv/venc/venc_v1.0/drv_venc_intf.c:        
    							vencTimer.function = (void *)VENC_TimerFunc;    // added (void *) by huxm 20241216
    	./msp/drv/venc/venc_v1.0/drv_venc_intf.c:    #if 0       // added by huxm 20241210
    	./msp/drv/venc/venc_v1.0/drv_venc_intf.c:    
    							vencTimer.function = (void *)VENC_TimerFunc;    // added (void *) by huxm 20241216
    	./msp/drv/venc/venc_v1.0/drv_venc_osal.c:    
    						#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)              // added by huxm 20241210
    	./msp/drv/venc/venc_v1.0/drv_venc_osal.c:    
    							#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/venc/venc_v1.0/drv_venc_osal.c:        
    								readlen = kernel_read(filp, buf, len, &filp->f_pos);    // added by huxm 20241210
    	./msp/drv/venc/venc_v1.0/drv_venc_osal.c:    
    							#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)        // added by huxm 20241210
    	./msp/drv/venc/venc_v1.0/drv_venc_osal.c:    
    							#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)          // added by huxm 20241210
    	./msp/drv/venc/venc_v1.0/drv_venc_osal.c:    
    							#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/venc/venc_v1.0/drv_venc_osal.c:        
    							writelen = kernel_write(filp, buf, len, &filp->f_pos);      // added by huxm 20241210
    	./msp/drv/venc/venc_v1.0/drv_venc_osal.c:    
    						#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/venc/venc_v1.0/drv_venc.h:// added by huxm 20241216 from "toolchain path"/linux/time.h
    	./msp/drv/sci/drv_sci_intf.c:    #if 0       // added by huxm 20241210
    	./msp/drv/sci/drv_sci_intf.c:    #if 0       // added by huxm 20241210
    	./msp/drv/hifb/src/drv_hifb_proc.c:    //while (pStr != '\0')  // delete by huxm 20241217
    	./msp/drv/hifb/src/drv_hifb_proc.c:    while (pStr != NULL)    // added by huxm 20241217
    	./msp/drv/hifb/src/drv_hifb_osr.c:// added by huxm 20241217 from "toolchain path"/linux/time.h
    	./msp/drv/hifb/src/drv_hifb_osr.c:// added by huxm 20241217
    	./msp/drv/hifb/src/drv_hifb_osr.c://#ifdef CONFIG_DMA_SHARED_BUFFER   // delete by huxm 20241217
    	./msp/drv/hifb/src/drv_hifb_osr.c:#ifndef CONFIG_DMA_SHARED_BUFFER    // added by huxm 20241217
    	./msp/drv/hifb/src/drv_hifb_osr.c://#ifdef CONFIG_DMA_SHARED_BUFFER   // delete by huxm 20241217
    	./msp/drv/hifb/src/drv_hifb_osr.c:#ifndef CONFIG_DMA_SHARED_BUFFER    // added by huxm 20241217
    	./msp/drv/hifb/src/drv_hifb_osr.c://#ifdef CONFIG_DMA_SHARED_BUFFER   // delete by huxm 20241217
    	./msp/drv/hifb/src/drv_hifb_osr.c:#ifndef CONFIG_DMA_SHARED_BUFFER    // added by huxm 20241217
    	./msp/drv/hifb/src/drv_hifb_dmabuf.c:    //struct hifb_memblock_pdata *pfbdata = NULL; // delete by huxm 20241217
    	./msp/drv/hifb/src/drv_hifb_dmabuf.c:    struct dma_buf_export_info *pfbdata = NULL;   // added by huxm 20241217
    	./msp/drv/hifb/src/drv_hifb_dmabuf.c:    // pfbdata->phys_base = phys_base;  // delete by huxm 20241217
    	./msp/drv/hifb/src/drv_hifb_dmabuf.c:    
    			// pfbbuf = dma_buf_export(pfbdata, &hifb_memblock_ops, size, flags, NULL); // delete by huxm 20241217
    	./msp/drv/hifb/src/drv_hifb_dmabuf.c:    pfbbuf = dma_buf_export(pfbdata);           // added by huxm 20241217
    	./msp/drv/vi/drv_vi_intf.c:    #if 0   // added by huxm 20241210
    	./msp/drv/vi/drv_vi_proc.c:    #if 0                    // delete by huxm 20241218
    	./msp/drv/vi/drv_vi_proc.c:    #else           // added by huxm 20241218
    	./msp/drv/vi/drv_vi_proc.c:    
    						//g_ViDrv[enPort][u32Chn].viTimer.data = (HI_LENGTH_T)(hVi);    // delete by huxm 20241216
    	./msp/drv/vi/drv_vi_proc.c:    //q->viTimer.data = (HI_LENGTH_T)(hVi);       // delete by huxm 20241216
    	./msp/drv/advca/drv_advca_intf.c:    #if 0   // added by huxm 20241210
    	./msp/drv/advca/V300/hal_advca_v300.c:// added by huxm 20241217 from "toolchain path"/linux/time.h
    	./msp/drv/advca/V300/hal_advca_v300.c:// added by huxm 20241217
    	./msp/drv/advca/runtime/runtime_module.c:    
    							#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)          // added by huxm 20241210
    	./msp/drv/advca/runtime/runtime_module.c:    
    							#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/advca/runtime/runtime_module.c:    
    							#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)        // added by huxm 20241210
    	./msp/drv/advca/runtime/runtime_module.c:    
    							#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/advca/runtime/runtime_module.c:       
    								 kernel_read(fp, pTmpbuf, MAX_IOMEM_SIZE-1, &pos);      // added by huxm 20241210
    	./msp/drv/advca/runtime/runtime_module.c:    
    							#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)        // added by huxm 20241210
    	./msp/drv/advca/runtime/runtime_module.c:   
    							 #if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)          // added by huxm 20241210
    	./msp/drv/advca/runtime/runtime_module.c:    
    							#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/advca/runtime/runtime_module.c:    
    							#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)        // added by huxm 20241210
    	./msp/drv/advca/runtime/runtime_module.c:    
    							#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/advca/runtime/runtime_module.c:        
    							kernel_read(fp, pTmpbuf, u32ReadLength, &pos);              // added by huxm 20241210
    	./msp/drv/advca/runtime/runtime_module.c:    
    							#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)        // added by huxm 20241210
    	./msp/drv/adec/adec_v1_1/drv_adec.c:        #if 0       // added by huxm 20241209
    	./msp/drv/mce/drv_mce_intf.c:    #if 0   // added by huxm 20241210
    	./msp/drv/mce/drv_mce_play.c:// added by huxm 20241209
    	./msp/drv/pm/hi_cpufreq.c:// added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:// end of added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    #if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)   // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    for_each_online_cpu(freqs.policy->cpu); // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    #else                                   // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    #endif                                  // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    #if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)   // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    for_each_online_cpu(freqs.policy->cpu);             // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    #else                               // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    #endif                              // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    #if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)   // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    
    					ret = cpufreq_frequency_table_target(policy,target_freq,relation); // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    #else                                               // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    #endif                                              // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    if (i < 100)                                // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    else                                        // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    current_target_freq = target_freq;          // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)           // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:
    				static int hi_cpufreq_verify(struct cpufreq_policy_data *policy_data)   // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:#else                                                         // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:#endif                                                       // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    #if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)       // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    
    						return cpufreq_frequency_table_verify(policy_data, freq_table); // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    #else                                                     // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    #endif                                                   // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:// added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:// extern int cpufreq_interactive_boostpulse(void);     // deleted by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    #if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)   // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:    #else   // added by huxm 20241217
    	./msp/drv/pm/hi_cpufreq.c:// added by huxm 20241217
    	./msp/drv/otp/drv_otp_intf.c:    #if 0           // modify by huxm 20241209
    	./msp/drv/gpu/mali700/drivers/gpu/arm/midgard/mali_kbase_core_linux.c:
    									//#include "mali_linux_trace.h"      // delete by huxm 20241219
    	./msp/drv/gpu/mali4xx/mali_kernel_common.h://#include "mali_osk.h"     // delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/mali_kernel_common.h:#include "linux/mali_osk.h"    // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/linux/mali_osk_notification.c:    #if 0   // modify by huxm 20241211
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_utilization.h:
    			#include "mali_utgard.h"   // delect linux/mali by huxm 20241211 #include <linux/mali/mali_utgard.h>
    	./msp/drv/gpu/mali4xx/linux/mali_memory_secure.c:                       #if 0   // delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/linux/mali_memory_secure.c:                       #else   // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/linux/mali_linux_trace.h:#if defined(CONFIG_TRACEPOINTS)          // added by huxm 20241215
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_linux.c:
    								//#include <linux/mali/mali_utgard_ioctl.h>          // delete by huxm 20241215
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_linux.c:#include "mali_utgard_ioctl.h"          // added by huxm 20241215
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_linux.c:
    									//#include <linux/mali/mali_utgard.h>           // delete by huxm 20241215
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_linux.c:
    									#include "mali_utgard.h"                         // added by huxm 20241215
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_linux.c:#define HAVE_COMPAT_IOCTL 1             // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_linux.c:#define HAVE_UNLOCKED_IOCTL 1   // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/linux/mali_osk_mali.h:
    				#include "mali_utgard.h"            // delete linux/mali by huxm 20241211 <linux/mali/mali_utgard.h>
    	./msp/drv/gpu/mali4xx/linux/mali_osk_mali.h:
    							#include "mali_osk.h"                       // delete <> by huxm 20241211 <mali_osk.h>
    	./msp/drv/gpu/mali4xx/linux/mali_osk_timers.c:  #if 0                   // delete by huxm 20241218
    	./msp/drv/gpu/mali4xx/linux/mali_osk_timers.c:  #else                   // added (void *) by huxm 20241218
    	./msp/drv/gpu/mali4xx/linux/mali_osk_timers.c:  
    								// tim->timer.data = (unsigned long)data;            // delect by huxm 20241211
    	./msp/drv/gpu/mali4xx/linux/mali_osk_timers.c:  #if     0               // added (void *) by huxm 20241211
    	./msp/drv/gpu/mali4xx/linux/mali_osk_timers.c:  
    								tim->timer.function = (void *)callback;      // added (void *) by huxm 20241208
    	./msp/drv/gpu/mali4xx/linux/mali_profiling_gator_api.h:
    							//#include <linux/mali/mali_utgard_profiling_gator_api.h>   // delete by huxm 20241215
    	./msp/drv/gpu/mali4xx/linux/mali_profiling_gator_api.h:
    									#include "mali_utgard_profiling_gator_api.h"  // added by huxm 20241215
    	./msp/drv/gpu/mali4xx/linux/mali_device_pause_resume.c:
    										//#include <linux/mali/mali_utgard.h>     // delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/linux/mali_device_pause_resume.c:#include "mali_utgard.h"      // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/linux/mali_memory_dma_buf.c:   //return PTR_RET(buf);          // delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/linux/mali_memory_dma_buf.c:   return PTR_ERR_OR_ZERO(buf);    // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/linux/mali_uk_types.h:
    						// delecte linux/mali/ by huxm 20241211 #include <linux/mali/mali_utgard_uk_types.h>
    	./msp/drv/gpu/mali4xx/linux/mali_ukk_mem.c:     # if 0 // delete by huxm 20241215
    	./msp/drv/gpu/mali4xx/linux/mali_ukk_mem.c:     #else // added by huxm 20241215
    	./msp/drv/gpu/mali4xx/linux/mali_ukk_mem.c:     # if 0 // delete by huxm 20241215
    	./msp/drv/gpu/mali4xx/linux/mali_ukk_mem.c:     #else // added by huxm 20241215
    	./msp/drv/gpu/mali4xx/linux/mali_profiling_events.h:
    							//#include <linux/mali/mali_utgard_profiling_events.h>    // delete by huxm 20241215
    	./msp/drv/gpu/mali4xx/linux/mali_profiling_events.h:
    									#include "mali_utgard_profiling_events.h"        // added by huxm 20241215
    	./msp/drv/gpu/mali4xx/linux/mali_osk_profiling.c://#include <mali_profiling_gator_api.h>// delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/linux/mali_osk_profiling.c:#include "mali_profiling_gator_api.h" // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/linux/mali_osk_profiling.c:
    										//#include "mali_linux_trace.h"           // delete by huxm 20241219
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_sysfs.c:
    										//#include <linux/mali/mali_utgard.h>       // delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_sysfs.c:
    										#include "mali_utgard.h"                    // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_sysfs.c:
    										//#include <linux/mali/mali_utgard.h>       // delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_sysfs.c:
    										#include "mali_utgard.h"                     // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/linux/mali_memory_cow.c:          #if 0   // delete by huxm 20241214
    	./msp/drv/gpu/mali4xx/linux/mali_memory_cow.c:          #else   // added by huxm 20241214
    	./msp/drv/gpu/mali4xx/linux/mali_memory_cow.c:                  #if 0   // delete by huxm 20241214
    	./msp/drv/gpu/mali4xx/linux/mali_memory_cow.c:                  #else   // added by huxm 20241214
    	./msp/drv/gpu/mali4xx/linux/mali_osk_time.c:#if 0               // delete by huxm 20241219
    	./msp/drv/gpu/mali4xx/linux/mali_osk_time.c:#else               // added by huxm 20241219
    	./msp/drv/gpu/mali4xx/linux/mali_memory_swap_alloc.c:
    								#define PAGE_CACHE_SHIFT   PAGE_SHIFT                  // added by huxm 20241214
    	./msp/drv/gpu/mali4xx/linux/mali_memory_swap_alloc.c:
    						#define PAGE_CACHE_SIZE            PAGE_SIZE                   // added by huxm 20241214
    	./msp/drv/gpu/mali4xx/linux/mali_memory_swap_alloc.c:
    						#define PAGE_CACHE_MASK            PAGE_MASK                   // added by huxm 20241214
    	./msp/drv/gpu/mali4xx/linux/mali_memory_swap_alloc.c:
    			#define PAGE_CACHE_ALIGN(addr)  (((addr)+PAGE_CACHE_SIZE-1)&PAGE_CACHE_MASK)// added by huxm 20241214
    	./msp/drv/gpu/mali4xx/linux/mali_memory_swap_alloc.c:
    						#define page_cache_get(page)               get_page(page)      // added by huxm 20241214
    	./msp/drv/gpu/mali4xx/linux/mali_memory_swap_alloc.c:
    							#define page_cache_release(page)   put_page(page)          // added by huxm 20241214
    	./msp/drv/gpu/mali4xx/linux/mali_memory_swap_alloc.c:   #if 0   // added by huxm 20241219
    	./msp/drv/gpu/mali4xx/linux/mali_memory_swap_alloc.c:   #else   // delete by huxm 20241219
    	./msp/drv/gpu/mali4xx/linux/mali_memory_swap_alloc.c:   #if 0   // added by huxm 20241219
    	./msp/drv/gpu/mali4xx/linux/mali_memory_swap_alloc.c:   #else   // delete by huxm 20241219
    	./msp/drv/gpu/mali4xx/linux/mali_memory.c:#if 0         // delete by huxm 20241212
    	./msp/drv/gpu/mali4xx/linux/mali_memory.c:      
    						unsigned long address = (unsigned long)vmf->virtual_address;    // delete by huxm 20241211
    	./msp/drv/gpu/mali4xx/linux/mali_memory.c:#else                 // added by huxm 20241212
    	./msp/drv/gpu/mali4xx/linux/mali_osk_mali.c:
    				#include "mali_utgard.h" // delect linux/mali by huxm 20241211 #include <linux/mali/mali_utgard.h>
    	./msp/drv/gpu/mali4xx/linux/mali_memory_os_alloc.c:             #if     0               // added by huxm 20241212
    	./msp/drv/gpu/mali4xx/linux/mali_memory_os_alloc.c:             #if 0   // delete by huxm 20241212
    	./msp/drv/gpu/mali4xx/linux/mali_memory_os_alloc.c:             #else   // addedby huxm 20241212
    	./msp/drv/gpu/mali4xx/linux/mali_memory_os_alloc.c:                            #if 0   // delete by huxm 20241212
    	./msp/drv/gpu/mali4xx/linux/mali_memory_os_alloc.c:                            #if 0   // delete by huxm 20241212
    	./msp/drv/gpu/mali4xx/linux/mali_memory_os_alloc.c:  
    						GFP_KERNEL, (unsigned long)&dma_attrs_wc); // added (unsigned long) by huxm 20241212
    	./msp/drv/gpu/mali4xx/linux/mali_memory_os_alloc.c: 
    								(unsigned long)&dma_attrs_wc);   // added (unsigned long) by huxm 20241212
    	./msp/drv/gpu/mali4xx/linux/mali_memory_os_alloc.c:                            
    		virt_arr[i], (dma_addr_t)phys_arr[i], (unsigned long)&dma_attrs_wc); // added (unsigned long) by huxm 20241212
    	./msp/drv/gpu/mali4xx/linux/mali_memory_os_alloc.c:     
    		dma_set_attr(DMA_ATTR_WRITE_COMBINE, (struct dma_attrs *)&dma_attrs_wc);       //added  by huxm 20241212
    	./msp/drv/gpu/mali4xx/linux/mali_memory_block_alloc.c:          #if 0   // delete by huxm 20241212
    	./msp/drv/gpu/mali4xx/linux/mali_memory_block_alloc.c:          #else   // addedby huxm 20241212
    	./msp/drv/gpu/mali4xx/common/mali_kernel_utilization.h:
    										//#include <linux/mali/mali_utgard.h>     // delete by huxm 20241215
    	./msp/drv/gpu/mali4xx/common/mali_kernel_utilization.h:#include "mali_utgard.h"    // added by huxm 20241215
    	./msp/drv/gpu/mali4xx/common/mali_osk_mali.h:
    								//#include <linux/mali/mali_utgard.h>              // delete by huxm 20241215
    	./msp/drv/gpu/mali4xx/common/mali_osk_mali.h:
    								#include "../linux/mali_utgard.h"                  // added by huxm 20241215
    	./msp/drv/gpu/mali4xx/common/mali_osk_mali.h://#include <mali_osk.h>              // delete by huxm 20241215
    	./msp/drv/gpu/mali4xx/common/mali_osk_mali.h:#include "mali_osk.h"             // added by huxm 20241215
    	./msp/drv/gpu/mali4xx/common/mali_profiling_gator_api.h:
    					//#include <linux/mali/mali_utgard_profiling_gator_api.h>     // delete by huxm 20241215
    	./msp/drv/gpu/mali4xx/common/mali_profiling_gator_api.h:
    								#include "mali_utgard_profiling_gator_api.h"    // added by huxm 20241215
    	./msp/drv/gpu/mali4xx/common/mali_uk_types.h:
    							// delecte linux/mali/ by huxm 20241211 #include <linux/mali/mali_utgard_uk_types.h>
    	./msp/drv/gpu/mali4xx/common/mali_group.c:// added by huxm 20241209
    	./msp/drv/gpu/mali4xx/common/mali_profiling_events.h:
    							//#include <linux/mali/mali_utgard_profiling_events.h>    // delete by huxm 20241215
    	./msp/drv/gpu/mali4xx/common/mali_profiling_events.h:
    										#include "mali_utgard_profiling_events.h"    // added by huxm 20241215
    	./msp/drv/gpu/mali4xx/common/mali_pp.c://#if defined(CONFIG_MALI400_PROFILING)  // delete by huxm 20241219
    	./msp/drv/gpu/mali4xx/common/mali_pp.c:#if !defined(CONFIG_MALI400_PROFILING)   // added by huxm 20241219
    	./msp/drv/gpu/mali4xx/common/mali_pp.c://#if defined(CONFIG_MALI400_PROFILING)          // delete by huxm 20241219
    	./msp/drv/gpu/mali4xx/common/mali_pp.c:#if !defined(CONFIG_MALI400_PROFILING)           // added by huxm 20241219
    	./msp/drv/gpu/mali4xx/common/mali_pp.c://#if defined(CONFIG_MALI400_PROFILING)          // delete by huxm 20241219
    	./msp/drv/gpu/mali4xx/common/mali_pp.c:#if !defined(CONFIG_MALI400_PROFILING)           // added by huxm 20241219
    	./msp/drv/gpu/mali4xx/common/mali_osk_profiling.h:
    										//#include "mali_linux_trace.h"             // delete by huxm 20241219
    	./msp/drv/gpu/mali4xx/common/mali_osk_profiling.h:// delete by huxm 20241219
    	./msp/drv/gpu/mali4xx/common/mali_gp.c://#if defined(CONFIG_MALI400_PROFILING)  // delete by huxm 20241219
    	./msp/drv/gpu/mali4xx/common/mali_gp.c:#if !defined(CONFIG_MALI400_PROFILING)   // added by huxm 20241219
    	./msp/drv/gpu/mali4xx/common/mali_gp.c://#if defined(CONFIG_MALI400_PROFILING)  // delete by huxm 20241219
    	./msp/drv/gpu/mali4xx/common/mali_gp.c:#if !defined(CONFIG_MALI400_PROFILING)   // added by huxm 20241219
    	./msp/drv/gpu/mali4xx/platform/mali400/mali4xx_core_scaling.c:
    										//#include <linux/mali/mali_utgard.h>     // delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali400/mali4xx_core_scaling.c:
    										#include "../../linux/mali_utgard.h"    // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali400/mali4xx_pmu.c:
    										//#include "linux/mali/mali_utgard.h"     // delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali400/mali4xx_pmu.c:#include "../../linux/mali_utgard.h"// added by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/arm/arm.c://#include "linux/mali/mali_utgard.h"     // delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/arm/arm.c:#include "../../linux/mali_utgard.h"    // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/arm/arm_core_scaling.c:
    									//#include "linux/mali/mali_utgard.h"     // delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/arm/arm_core_scaling.c:
    										#include "../../linux/mali_utgard.h"//added by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx_core_scaling.c:
    										//#include "linux/mali/mali_utgard.h"     // delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx_core_scaling.c:
    										#include "../../linux/mali_utgard.h"    // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx_pmu.h:
    										//#include "mali_hw_core.h"              // delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx_pmu.h:
    										#include "../../linux/mali_hw_core.h"    // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx_pmu.h:
    										//#include "mali_osk.h"                 // delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx_pmu.h:#include "../../linux/mali_osk.h" // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx_clk.c:
    										//#include "linux/mali/mali_utgard.h"     // delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx_clk.c:
    										#include "../../linux/mali_utgard.h"    // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx_clk.c://#include "mali_hw_core.h"     // delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx_clk.c:
    									#include "../../linux/mali_hw_core.h"    // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx_pmu.c:
    									//#include "linux/mali/mali_utgard.h"     // delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx_pmu.c:
    											#include "../../linux/mali_utgard.h"    // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx_pmu.c://#include "mali_pmu.h"           // delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx_pmu.c:#include "../../linux/mali_pmu.h"   // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx.c:
    										//#include <linux/mali/mali_utgard.h>     // delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx.c:#include "../../linux/mali_utgard.h"    // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx.c://#include "mali_osk.h"     // delete by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx.c:#include "../../linux/mali_osk.h"    // added by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx.c:// added by huxm 20241216
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx.c:    #if 0   // delete by huxm 20241219
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx.c:    #else   // added by huxm 20241219
    	./msp/drv/adsp/adsp_v1_1/kfile_ops_func.c:   
    							 #if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)        // added by huxm 20241210
    	./msp/drv/adsp/adsp_v1_1/kfile_ops_func.c:    
    							#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/adsp/adsp_v1_1/kfile_ops_func.c:       
    								 readlen = kernel_read(filp, buf, len, &filp->f_pos);    // added by huxm 20241210
    	./msp/drv/adsp/adsp_v1_1/kfile_ops_func.c:    
    							#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)        // added by huxm 20241210
    	./msp/drv/adsp/adsp_v1_1/kfile_ops_func.c:    
    						#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/adsp/adsp_v1_1/kfile_ops_func.c:    
    						#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)              // added by huxm 20241210
    	./msp/drv/adsp/adsp_v1_1/kfile_ops_func.c:       
    							 writelen = kernel_write(filp, buf, len, &filp->f_pos);      // added by huxm 20241210
    	./msp/drv/adsp/adsp_v1_1/kfile_ops_func.c:    
    						#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/adsp/adsp_v1_1/kfile_ops_func.c:    
    						#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)              // added by huxm 20241210
    	./msp/drv/adsp/adsp_v1_1/kfile_ops_func.c:       
    							 seeklen = vfs_llseek(filp, offset, origin);                 // added by huxm 20241210
    	./msp/drv/adsp/adsp_v1_1/kfile_ops_func.c:    
    						#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/adsp/adsp_v1_1/osal/adsp_osal.c:
    					extern unsigned long long notrace sched_clock(void);                   // added by huxm 20241209
    	./msp/drv/adsp/adsp_v1_1/osal/adsp_osal.c:    #if 0                     // delete by huxm 20241218
    	./msp/drv/adsp/adsp_v1_1/osal/adsp_osal.c:    #else           // added by huxm 20241218
    	./msp/drv/demux/demux_v2/drv_demux_intf.c:            
    								#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20241217
    	./msp/drv/demux/demux_v2/drv_demux_intf.c:            
    								#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20241217
    	./msp/drv/demux/demux_v2/drv_demux_intf.c:            
    								#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20241217
    	./msp/drv/demux/demux_v2/drv_demux_intf.c:            
    								#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20241217
    	./msp/drv/demux/demux_v2/drv_demux_intf.c:   
    								 #if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)      // added by huxm 20241209
    	./msp/drv/demux/demux_v2/drv_demux_intf.c:   
    								 #if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)      // added by huxm 20241209
    	./msp/drv/demux/demux_v2/drv_demux.c:                #if 0       // added by huxm 20241209
    	./msp/drv/demux/demux_v2/drv_demux.c:            #if 0       // added by huxm 20241209
    	./msp/drv/demux/demux_v2/drv_demux.c:    #if 0       // added by huxm 20241209
    	./msp/drv/demux/demux_v2/drv_demux.c:    #if 0       // added by huxm 20241209
    	./msp/drv/demux/demux_v2/drv_demux_func.c:   
    								 #if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20241217
    	./msp/drv/demux/demux_v2/drv_demux_func.c:    
    								#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20241217
    	./msp/drv/demux/demux_v2/drv_demux_func.c:    
    								#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20241217
    	./msp/drv/demux/demux_v2/drv_demux_func.c:    
    								#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20241217
    	./msp/drv/demux/demux_v2/drv_demux_func.c:    
    							#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20241217
    	./msp/drv/frontend/qtc/sv_unf_osal.c:        
    							#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)        // added by huxm 20241210
    	./msp/drv/frontend/qtc/sv_unf_osal.c:    
    						#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/frontend/qtc/sv_unf_osal.c:        
    							readlen = kernel_read(filp, buf, len, &filp->f_pos);    // added by huxm 20241210
    	./msp/drv/frontend/qtc/sv_unf_osal.c:    
    							#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)        // added by huxm 20241210
    	./msp/drv/frontend/qtc/sv_unf_osal.c:       
    						 #if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/frontend/qtc/sv_unf_osal.c:    
    						#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)              // added by huxm 20241210
    	./msp/drv/frontend/qtc/sv_unf_osal.c:        
    							writelen = kernel_write(filp, buf, len, &filp->f_pos);      // added by huxm 20241210
    	./msp/drv/frontend/qtc/sv_unf_osal.c:   
    						 #elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/frontend/qtc/sv_unf_osal.c:    
    						#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/frontend/qtc/sv_unf_osal.c:    
    						#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)              // added by huxm 20241210
    	./msp/drv/frontend/qtc/sv_unf_osal.c:        
    							seeklen = vfs_llseek(filp, offset, origin);                 // added by huxm 20241210
    	./msp/drv/frontend/qtc/sv_unf_osal.c:    
    						#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/frontend/drv_tuner.c:    #if 0           // modify by huxm 20241209
    	./msp/drv/frontend/drv_tuner.c:    #if 0       // added by huxm 20241210
    	./msp/drv/frontend/drv_tuner.c:    #if 0       // added by huxm 20241210
    	./msp/drv/frontend/drv_tuner.c:    #if 0   // added by huxm 20241210
    	./msp/drv/frontend/demod/MXL254/MxL_HRCLS_OEM_Drv.c:    #if 0 // added by huxm 20241210
    	./msp/drv/frontend/demod/MXL254/MxL_HRCLS_OEM_Drv.c:    #if 0           // modify by huxm 20241210
    	./msp/drv/frontend/demod/MXL254/MxL_HRCLS_OEM_Drv.c:    #if 0   // added by huxm 20241210
    	./msp/drv/keyled/keyled_gpiokey/drv_keyled_gpiokey.c:        #if 0                      // delete by huxm 20241219
    	./msp/drv/keyled/keyled_gpiokey/drv_keyled_gpiokey.c:        #else                      // added by huxm 20241219
    	./msp/drv/keyled/keyled_pt6964/drv_keyled_pt6964.c:
    						//static HI_VOID hi_pt6964_keyled_scan(unsigned long data);    // delete by huxm 20241217
    	./msp/drv/keyled/keyled_pt6964/drv_keyled_pt6964.c:
    						static HI_VOID hi_pt6964_keyled_scan(struct timer_list *data);    // added by huxm 20241217
    	./msp/drv/keyled/keyled_pt6964/drv_keyled_pt6964.c:
    				//static DEFINE_TIMER(keyled_scan_timer, hi_pt6964_keyled_scan, 0, 0);   // delete by huxm 20241217
    	./msp/drv/keyled/keyled_pt6964/drv_keyled_pt6964.c:
    				static DEFINE_TIMER(keyled_scan_timer, hi_pt6964_keyled_scan);           // added by huxm 20241217
    	./msp/drv/keyled/keyled_pt6964/drv_keyled_pt6964.c:
    				//static HI_VOID keyled_dotflash_handler_pt6964(unsigned long data)      // delete by huxm 20241217
    	./msp/drv/keyled/keyled_pt6964/drv_keyled_pt6964.c:
    				static HI_VOID keyled_dotflash_handler_pt6964(struct timer_list *data)   // added by huxm 20241217
    	./msp/drv/keyled/keyled_pt6964/drv_keyled_pt6964.c:
    				//static HI_VOID hi_pt6964_keyled_scan(unsigned long data);              // delete by huxm 20241217
    	./msp/drv/keyled/keyled_pt6964/drv_keyled_pt6964.c:
    				static HI_VOID hi_pt6964_keyled_scan(struct timer_list *data)           // added by huxm 20241217
    	./msp/drv/keyled/keyled_pt6964/drv_keyled_pt6964.c:    #if 0                    // delete by huxm 20241218
    	./msp/drv/keyled/keyled_pt6964/drv_keyled_pt6964.c:    #else                    // added by huxm 20241218
    	./msp/drv/keyled/keyled_fd650/drv_keyled_fd650.c:
    				//static HI_VOID hi_fd650_keyled_scan(unsigned long data);              // delete by huxm 20241217
    	./msp/drv/keyled/keyled_fd650/drv_keyled_fd650.c:
    				static HI_VOID hi_fd650_keyled_scan(struct timer_list * data);          // added by huxm 20241217
    	./msp/drv/keyled/keyled_fd650/drv_keyled_fd650.c:
    				//static DEFINE_TIMER(keyled_scan_timer, hi_fd650_keyled_scan, 0, 0);   // delete by huxm 20241217
    	./msp/drv/keyled/keyled_fd650/drv_keyled_fd650.c:
    				static DEFINE_TIMER(keyled_scan_timer, hi_fd650_keyled_scan);           // added by huxm 20241217
    	./msp/drv/keyled/keyled_fd650/drv_keyled_fd650.c:
    						//static HI_VOID hi_fd650_keyled_scan(unsigned long data)       // delete by huxm 20241217
    	./msp/drv/keyled/keyled_fd650/drv_keyled_fd650.c:
    						static HI_VOID hi_fd650_keyled_scan(struct timer_list * data)  // added by huxm 20241217
    	./msp/drv/keyled/keyled_fd650/drv_keyled_fd650.c:
    				// static HI_VOID keyled_dotflash_handler_fd650(unsigned long data)     // delete by huxm 20241217
    	./msp/drv/keyled/keyled_fd650/drv_keyled_fd650.c:
    				static HI_VOID keyled_dotflash_handler_fd650(struct timer_list * data)  // added  by huxm 20241217
    	./msp/drv/keyled/keyled_fd650/drv_keyled_fd650.c:    #if 0                      // delete by huxm 20241218
    	./msp/drv/keyled/keyled_fd650/drv_keyled_fd650.c:    #else                      // added by huxm 20241218
    	./msp/drv/keyled/keyled_std/drv_keyled_std.c:    
    					sleep_timer.function = (void *)keyled_timeout_handler;      // added (void *) by huxm 20241208
    	./msp/drv/keyled/keyled_std/drv_keyled_std.c:    #if 0                  // delete by huxm 20241218
    	./msp/drv/keyled/keyled_std/drv_keyled_std.c:    #else                  // added by huxm 20241218
    	./msp/drv/keyled/keyled_std/drv_keyled_std.c:    
    				dotflash_timer.function = (void *)keyled_dotflash_handler;      // added (void *) by huxm 20241208
    	./msp/drv/keyled/keyled_std/drv_keyled_std.c:    #if 0                  // delete by huxm 20241218
    	./msp/drv/keyled/keyled_std/drv_keyled_std.c:    #else                  // added by huxm 20241218
    	./msp/drv/keyled/drv_keyled_intf.c:    #if 0           // modify by huxm 20241210
    	./msp/drv/keyled/keyled_ct1642/drv_keyled_ct1642_inner.c:
    					//static HI_VOID keyled_timeout_handler(unsigned long data)       // delete by huxm 20241217
    	./msp/drv/keyled/keyled_ct1642/drv_keyled_ct1642_inner.c:
    						static HI_VOID keyled_timeout_handler(struct timer_list *data)    // added by huxm 20241217
    	./msp/drv/keyled/keyled_ct1642/drv_keyled_ct1642_inner.c:
    				//static HI_VOID keyled_dotflash_handler(unsigned long data)      // delete by huxm 20241217
    	./msp/drv/keyled/keyled_ct1642/drv_keyled_ct1642_inner.c:
    					static HI_VOID keyled_dotflash_handler(struct timer_list *data)      // added by huxm 20241217
    	./msp/drv/keyled/keyled_ct1642/drv_keyled_ct1642_inner.c:    #if 0                      // delete by huxm 20241219
    	./msp/drv/keyled/keyled_ct1642/drv_keyled_ct1642_inner.c:    #else                      // added by huxm 20241219
    	./msp/drv/keyled/keyled_ct1642/drv_keyled_ct1642_inner.c:    #if 0                      // delete by huxm 20241219
    	./msp/drv/keyled/keyled_ct1642/drv_keyled_ct1642_inner.c:    #else                      // added by huxm 20241219
    	./msp/drv/keyled/keyled_ct1642/drv_keyled_ct1642.c:        #if 0                        // delete by huxm 20241219
    	./msp/drv/keyled/keyled_ct1642/drv_keyled_ct1642.c:        #else                        // added by huxm 20241219
    	./msp/drv/keyled/keyled_pt6961/drv_keyled_pt6961.c:
    					//static HI_VOID hi_pt6961_keyled_scan(unsigned long data);         // delete by huxm 20241217
    	./msp/drv/keyled/keyled_pt6961/drv_keyled_pt6961.c:
    					static HI_VOID hi_pt6961_keyled_scan(struct timer_list *data);      // added by huxm 20241217
    	./msp/drv/keyled/keyled_pt6961/drv_keyled_pt6961.c:
    				//static DEFINE_TIMER(keyled_scan_timer, hi_pt6961_keyled_scan, 0, 0);    // delete by huxm 20241217
    	./msp/drv/keyled/keyled_pt6961/drv_keyled_pt6961.c:
    				static DEFINE_TIMER(keyled_scan_timer, hi_pt6961_keyled_scan);            // added by huxm 20241217
    	./msp/drv/keyled/keyled_pt6961/drv_keyled_pt6961.c:
    					//static HI_VOID hi_pt6961_keyled_scan(unsigned long data);         // delete by huxm 20241217
    	./msp/drv/keyled/keyled_pt6961/drv_keyled_pt6961.c:
    					static HI_VOID hi_pt6961_keyled_scan(struct timer_list *data)      // added by huxm 20241217
    	./msp/drv/gpio/drv_gpio.c:// added added by huxm 20241212
    	./msp/drv/gpio/drv_gpio.c:// end of added by huxm 20241212
    	./msp/drv/vo/vdp_v4_0/drv_disp_intf.c:    #if 0           // modify by huxm 20241210
    	./msp/drv/vo/vdp_v4_0/drv_disp_intf.c:    #if 0           // modify by huxm 20241210
    	./msp/drv/vo/vdp_v4_0/com/drv_disp_debug.c:        #if 0       // added by huxm 20241210
    	./msp/drv/vo/vdp_v4_0/com/drv_disp_debug.c:        #if 0       // added by huxm 20241210
    	./msp/drv/vo/vdp_v4_0/com/drv_disp_debug.c:        #if 0       // added by huxm 20241210
    	./msp/drv/vo/vdp_v4_0/com/drv_disp_debug.c:        #if 0       // added by huxm 20241210
    	./msp/drv/vo/vdp_v4_0/drv_win_intf.c:    #if 0           // modify by huxm 20241210
    	./msp/drv/vo/vdp_v3_0/drv_disp_intf.c:    #if 0           // modify by huxm 20241210
    	./msp/drv/vo/vdp_v3_0/drv/drv_disp_isr.c:// added by huxm 20241209
    	./msp/drv/vo/vdp_v3_0/com/drv_disp_debug.c:        #if 0       // added by huxm 20241210
    	./msp/drv/vo/vdp_v3_0/com/drv_disp_debug.c:        #if 0       // added by huxm 20241210
    	./msp/drv/vo/vdp_v3_0/com/drv_disp_debug.c:        #if 0       // added by huxm 20241210
    	./msp/drv/vo/vdp_v3_0/com/drv_disp_debug.c:        #if 0       // added by huxm 20241210
    	./msp/drv/vo/vdp_v3_0/com/drv_disp_debug.c:    #if 0   // added by huxm 20241210
    	./msp/drv/vo/vdp_v3_0/drv_win_intf.c:    #if 0           // modify by huxm 20241210
    	./msp/drv/vo/vdp_v2_0/drv_disp_intf.c:    #if 0           // modify by huxm 20241210
    	./msp/drv/vo/vdp_v2_0/drv/drv_display.c:memcpy(u32macv, g_O5_u8MacvTable, 5*sizeof(HI_U32));
    											// memcpy(u32macv, g_O5_u8MacvTable, 5)modify by huxm 20241217
    	./msp/drv/vo/vdp_v2_0/drv/drv_display.c:       
    					 memset(u32macv, 0x0, 5*sizeof(HI_U32));  // memset(u32macv, 0x0, 5) modify by huxm 20241217
    	./msp/drv/vo/vdp_v2_0/com/drv_disp_debug.c:    
    						#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)              // added by huxm 20241210
    	./msp/drv/vo/vdp_v2_0/com/drv_disp_debug.c:    
    							#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/vo/vdp_v2_0/com/drv_disp_debug.c:        
    								readlen = kernel_read(filp, buf, len, &filp->f_pos);    // added by huxm 20241210
    	./msp/drv/vo/vdp_v2_0/com/drv_disp_debug.c:    
    							#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)        // added by huxm 20241210
    	./msp/drv/vo/vdp_v2_0/com/drv_disp_debug.c:    
    						#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)              // added by huxm 20241210
    	./msp/drv/vo/vdp_v2_0/com/drv_disp_debug.c:    
    						#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)              // added by huxm 20241210
    	./msp/drv/vo/vdp_v2_0/com/drv_disp_debug.c:        
    							writelen = kernel_write(filp, buf, len, &filp->f_pos);      // added by huxm 20241210
    	./msp/drv/vo/vdp_v2_0/com/drv_disp_debug.c:    
    						#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/vo/vdp_v2_0/com/drv_disp_debug.c:    #if 0   // delete by huxm 20241216
    	./msp/drv/vo/vdp_v2_0/com/drv_disp_debug.c:    #else   // added by huxm 20241216
    	./msp/drv/vo/vdp_v2_0/drv_disp.c:            #if 0   // delete by huxm 20241216
    	./msp/drv/vo/vdp_v2_0/drv_disp.c:            #else   // added by huxm 20241216
    	./msp/drv/vo/vdp_v2_0/drv_win_intf.c:    #if 0       // delete by huxm 20241216
    	./msp/drv/vo/vdp_v2_0/drv_win_intf.c:    #else       // added by huxm 20241216
    	./msp/drv/vo/vdp_v2_0/hal/3798m/vdp_driver.c:// added by huxm 20241208
    	./msp/drv/hdmi/hdmi_2_0/drv_hdmi_debug.c:    
    							#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)          // added by huxm 20241210
    	./msp/drv/hdmi/hdmi_2_0/drv_hdmi_debug.c:    
    							#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/hdmi/hdmi_2_0/drv_hdmi_debug.c:       
    								 readlen = kernel_read(filp, buf, len, &filp->f_pos);    // added by huxm 20241210
    	./msp/drv/hdmi/hdmi_2_0/drv_hdmi_debug.c:    
    							#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)        // added by huxm 20241210
    	./msp/drv/hdmi/hdmi_2_0/drv_hdmi_debug.c:    
    						#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)              // added by huxm 20241210
    	./msp/drv/hdmi/hdmi_2_0/drv_hdmi_debug.c:   
    						 #if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)              // added by huxm 20241210
    	./msp/drv/hdmi/hdmi_2_0/drv_hdmi_debug.c:       
    							 writelen = kernel_write(filp, buf, len, &filp->f_pos);      // added by huxm 20241210
    	./msp/drv/hdmi/hdmi_2_0/drv_hdmi_debug.c:    
    						#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/hdmi/hdmi_2_0/osal/hisiv200/hdmi_osal.c:
    					#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)                  // added by huxm 20241210
    	./msp/drv/hdmi/hdmi_2_0/osal/hisiv200/hdmi_osal.c:
    				#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)                      // added by huxm 20241210
    	./msp/drv/hdmi/hdmi_2_0/osal/hisiv200/hdmi_osal.c:    
    					s32ReadLen = kernel_read(pFile, ps8Buf, u32Len, &pFile->f_pos);     // added by huxm 20241210
    	./msp/drv/hdmi/hdmi_2_0/osal/hisiv200/hdmi_osal.c:
    								#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)   // added by huxm 20241210
    	./msp/drv/hdmi/hdmi_2_0/osal/hisiv200/hdmi_osal.c:
    					#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)                  // added by huxm 20241210
    	./msp/drv/hdmi/hdmi_2_0/osal/hisiv200/hdmi_osal.c:
    						#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)               // added by huxm 20241210
    	./msp/drv/hdmi/hdmi_2_0/osal/hisiv200/hdmi_osal.c:   
    					 s32WriteLen = kernel_write(pFile, ps8Buf, u32Len, &pFile->f_pos); // added by huxm 20241210
    	./msp/drv/hdmi/hdmi_2_0/osal/hisiv200/hdmi_osal.c:
    							#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)      // added by huxm 20241210
    	./msp/drv/hdmi/hdmi_2_0/osal/hisiv200/hdmi_osal.c:// added by huxm 20241209
    	./msp/drv/hdmi/hdmi_1_4/hdmi_intf.c:    #if 0       // added by huxm 20241210
    	./msp/drv/hdmi/hdmi_1_4/hdmi_drv/si_timer.h:#include <linux/kernel.h>   //added by huxm 20241208
    	./msp/drv/hdmi/hdmi_1_4/hdmi_drv/si_timer.h:// added by huxm 20241208 from "toolchain path"/linux/time.h
    	./msp/drv/hdmi/hdmi_1_4/hdmi_drv/si_timer.c:// added by huxm 20241216
    	./msp/drv/pwm/drv_pwm_intf.c:    #if 0       // added by huxm 20241210
    	./msp/drv/omxvdec/omxvdec_v2.0/processor_vpss.c:
    							#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)        // added by huxm 20241210
    	./msp/drv/omxvdec/omxvdec_v2.0/processor_vpss.c:
    							#elif LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20241210
    	./msp/drv/omxvdec/omxvdec_v2.0/processor_vpss.c:
    							#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)        // added by huxm 20241210
    	./msp/drv/omxvdec/omxvdec_v2.0/processor_vpss.c:
    							#elif LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20241210
    	./msp/drv/omxvdec/omxvdec_v2.0/processor_vpss.c:
    							#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)        // added by huxm 20241210
    	./msp/drv/omxvdec/omxvdec_v2.0/processor_vpss.c:
    							#elif LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20241210
    	./msp/drv/omxvdec/omxvdec_v2.0/processor_vpss.c:
    							#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)        // added by huxm 20241210
    	./msp/drv/omxvdec/omxvdec_v2.0/processor_vpss.c:
    							#elif LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20241210
    	./msp/drv/omxvdec/omxvdec_v2.0/omxvdec.c:// added by huxm 20241209
    	./msp/drv/omxvdec/omxvdec_v2.0/channel.c:    
    						#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/omxvdec/omxvdec_v2.0/channel.c:    
    						#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)              // added by huxm 20241210
    	./msp/drv/omxvdec/omxvdec_v2.0/channel.c: kernel_write(g_SaveRawFile, pstream->kern_vaddr, 
    											pstream->act_len, &g_SaveRawFile->f_pos);// added by huxm 20241210
    	./msp/drv/omxvdec/omxvdec_v2.0/channel.c:    
    						#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/omxvdec/omxvdec_v1.0/channel.c:        #if 0       // added by huxm 20241210
    	./msp/drv/omxvdec/omxvdec_v1.0/channel.c:        #if 0       // added by huxm 20241210
    	./msp/drv/vad/sil9293/drv_sil9293_intf.c:    #if 0       // added by huxm 20241210
    	./msp/drv/tde/src/tde_osr_k.c:// #define TDE_IOCTL_FUNC_NUM     
    						(sizeof(g_paTdeCtlFuncDispatchItem)/sizeof(HI_U32*))          // delete by huxm 20241217
    	./msp/drv/tde/src/tde_osr_k.c:#define TDE_IOCTL_FUNC_NUM   
    	          (sizeof(g_paTdeCtlFuncDispatchItem)/sizeof(TDE_CTL_FUNC_DISPATCH_ITEM))     // added by huxm 20241217
    	./msp/drv/tde/src/tde_osr_k.c:#ifdef MODIFY_BY_HUXM_20241208
    	./msp/drv/vpss/vpss_v3_0/vpss_osal.c:        
    							#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)        // added by huxm 20241210
    	./msp/drv/vpss/vpss_v3_0/vpss_osal.c:    
    							#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/vpss/vpss_v3_0/vpss_osal.c:        
    								readlen = kernel_read(filp, buf, len, &filp->f_pos);    // added by huxm 20241210
    	./msp/drv/vpss/vpss_v3_0/vpss_osal.c:    
    							#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)        // added by huxm 20241210
    	./msp/drv/vpss/vpss_v3_0/vpss_osal.c:    
    						#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/vpss/vpss_v3_0/vpss_osal.c:    
    						#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)              // added by huxm 20241210
    	./msp/drv/vpss/vpss_v3_0/vpss_osal.c:       
    							 writelen = kernel_write(filp, buf, len, &filp->f_pos);      // added by huxm 20241210
    	./msp/drv/vpss/vpss_v3_0/vpss_osal.c:    
    						#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/vpss/vpss_v3_0/vpss_osal.c:    #if     0   // added by huxm 20241210
    	./msp/drv/vpss/vpss_v3_0/hal/hi3798mv100/vpss_reg_3798m.h:
    					//HI_S32 VPSS_REG_SetDIR(HI_U32 u32AppAddr,HI_S32 s32MultDir[15]);  // delete by huxm 20241217
    	./msp/drv/vpss/vpss_v3_0/hal/hi3798mv100/vpss_reg_3798m.h:
    					HI_S32 VPSS_REG_SetDIR(HI_U32 u32AppAddr,HI_S32 *s32MultDir);       // added by huxm 20241217
    	./msp/drv/vpss/vpss_v3_0/hal/hi3798mv100/vpss_reg_3798m.h:
    					//HI_S32 VPSS_REG_SetIntpSclRat(HI_U32 u32AppAddr,HI_S32 s32Rat[15]); // delete by huxm 20241217
    	./msp/drv/vpss/vpss_v3_0/hal/hi3798mv100/vpss_reg_3798m.h:
    					HI_S32 VPSS_REG_SetIntpSclRat(HI_U32 u32AppAddr,HI_S32 *s32Rat);    // added by huxm 20241217
    	./msp/drv/vpss/vpss_v3_0/hal/hi3798mv100/vpss_reg_3798m.h:
    				//HI_S32 VPSS_REG_SetMotionDiffThd(HI_U32 u32AppAddr,HI_S32 s32Thd[8]);   // delete by huxm 20241217
    	./msp/drv/vpss/vpss_v3_0/hal/hi3798mv100/vpss_reg_3798m.h:
    					HI_S32 VPSS_REG_SetMotionDiffThd(HI_U32 u32AppAddr,HI_S32 *s32Thd);   // added by huxm 20241217
    	./msp/drv/vpss/vpss_v3_0/hal/hi3798mv100/vpss_reg_3798m.h:
    				//HI_S32 VPSS_REG_SetRecFldStep(HI_U32 u32AppAddr,HI_S32 s32Step[2]);     // delete by huxm 20241217
    	./msp/drv/vpss/vpss_v3_0/hal/hi3798mv100/vpss_reg_3798m.h:
    				HI_S32 VPSS_REG_SetRecFldStep(HI_U32 u32AppAddr,HI_S32 *s32Step);       // added by huxm 20241217
    	./msp/drv/vpss/vpss_v3_0/hal/hi3798mv100/vpss_reg_3798m.h:
    				//HI_S32 VPSS_REG_SetRecFrmStep(HI_U32 u32AppAddr,HI_S32 s32Step[2]);     // delete by huxm 20241217
    	./msp/drv/vpss/vpss_v3_0/hal/hi3798mv100/vpss_reg_3798m.h:
    				HI_S32 VPSS_REG_SetRecFrmStep(HI_U32 u32AppAddr,HI_S32 *s32Step);       // added by huxm 20241217
    	./msp/drv/vpss/vpss_v4_0/vpss_osal.c:        #if 0       // added by huxm 20241210
    	./msp/drv/vpss/vpss_v4_0/vpss_osal.c:        #if 0       // added by huxm 20241210
    	./msp/drv/vpss/vpss_v4_0/vpss_osal.c:        #if 0       // added by huxm 20241210
    	./msp/drv/vpss/vpss_v4_0/vpss_osal.c:        #if 0       // added by huxm 20241210
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:     
    				//if (copy_to_user((HI_VOID *)arg, (HI_VOID *)&DecHandle,sizeof(HI_U64))) // delete by huxm 20241217
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:     
    				if (copy_to_user((HI_VOID *)arg, (HI_VOID *)&DecHandle,sizeof(HI_U32)))   // added by huxm 20241217
    	./msp/drv/i2c/gpio_i2c/drv_gpio_i2c.c: * // added by huxm 20241209
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_intf_k.c:    #if 0                    // delete by huxm 20241218
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_intf_k.c:    #else                    // added by huxm 20241218
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_intf.c:    #if     0   // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_intf.c:            #if     0   // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_intf.c:            #if 0   // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_intf.c:            #if 0   // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:   
    						#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:    
    						#elif LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:            
    						#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:           
    						 #elif LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:    
    						#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:   
    						 #elif LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:    
    						#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:    
    						#elif LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:                
    						#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:               
    						 #elif LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:        
    						#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:        
    						#elif LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:                    
    						#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:                    
    						#elif LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:                    
    						#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:                   
    						 #elif LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:                   
    						 #if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:                    
    						#elif LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:                    
    						#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:                    
    						#elif LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:        
    						#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_buf_mng.c:        
    						#elif LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/vdec/vdec_v2.0/drv_vdec_intf.c:    #if 0       // added by huxm 20241210
    	./msp/drv/vdec/vdec_v2.0/drv_vdec_buf_mng.c:    #if 0       // added by huxm 20241210
    	./msp/drv/vdec/vdec_v2.0/drv_vdec_buf_mng.c:            #if 0   //added by huxm 20241210
    	./msp/drv/vdec/vdec_v2.0/drv_vdec_buf_mng.c:    #if 0   //added by huxm 20241210
    	./msp/drv/vdec/vdec_v2.0/drv_vdec_buf_mng.c:    #if 0       // added by huxm 20241210
    	./msp/drv/vdec/vdec_v2.0/drv_vdec_buf_mng.c:            #if 0   //added by huxm 20241210
    	./msp/drv/vdec/vdec_v2.0/drv_vdec_buf_mng.c:    #if 0   //added by huxm 20241210
    	./msp/drv/vdec/vdec_v2.0/drv_vdec_buf_mng.c:            #if 0   // added by huxm 20241210
    	./msp/drv/vdec/vdec_v2.0/drv_vdec_buf_mng.c:    #if 0   //added by huxm 20241210
    	./msp/drv/vdec/vdec_v2.0/drv_vdec_buf_mng.c:            #if 0   //added by huxm 20241210
    	./msp/drv/vdec/vdec_v2.0/drv_vdec_buf_mng.c:            #if 0   //added by huxm 20241210
    	./msp/drv/vdec/vdec_v2.0/drv_vdec_buf_mng.c:    #if 0       // added by huxm 20241210
    	./msp/drv/vdec/vdec_v2.0/drv_vdec_buf_mng.c:        #if 0   //added by huxm 20241210
    	./msp/drv/aiao/aiao_v1_1/ai/drv_ai.c:    #if 0   // modify by huxm 20241209
    	./msp/drv/aiao/aiao_v1_1/ai/drv_ai.c:        #if 0       // added by huxm 20241209
    	./msp/drv/aiao/aiao_v1_1/ao/drv_ao_op.c:    #if 0                       // delete by huxm 20241218
    	./msp/drv/aiao/aiao_v1_1/ao/drv_ao_op.c:    #else                       // added by huxm 20241218
    	./msp/drv/aiao/aiao_v1_1/ao/drv_ao_op.c:    
    					//pCard->stMuteDisableTimer.data = (HI_U8*)pCard - (HI_U8*)(HI_NULL); // delete by huxm 20241209
    	./msp/drv/aiao/aiao_v1_1/ao/drv_ao_op.c:// added by huxm 20241209
    	./msp/drv/aiao/aiao_v1_1/ao/drv_ao.c:        #if 0       // added by huxm 20241209
    	./msp/drv/aiao/aiao_v1_1/ao/drv_ao.c:        #if 0       // added by huxm 20241209
    	./msp/drv/aiao/aiao_v1_1/ao/drv_ao.c:    #if 0       // modify by huxm 20241209
    	./msp/drv/aiao/aiao_v1_1/ao/drv_ao_track.c:        #if 0       // added by huxm 20241209
    	./msp/drv/aiao/aiao_v1_1/common/src/hal_aiao_func.c:    // modify by huxm 20241209
    	./msp/drv/aiao/aiao_v1_1/common/src/audio_util.c:// added by huxm 20241208 from "toolchain path"/linux/time.h
    	./msp/drv/vfmw/softlib/Makefile:#delete -mcpu=cortex-a9 by huxm 20241209
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/Makefile:#delete -mcpu=cortex-a9 by huxm 20241209
    	./msp/drv/vfmw/vfmw_v5.0/scene/tvp/client/vfmw_tee_client.c:        #if 0       // added by huxm 20241210
    	./msp/drv/vfmw/vfmw_v5.0/scene/tvp/client/vfmw_tee_client.c:        #if 0       // added by huxm 20241210
    	./msp/drv/vfmw/vfmw_v5.0/firmware/osal/linux_kernel/vfmw_osal.c:
    												#include<linux/kernel.h>    //added by huxm 20241209
    	./msp/drv/vfmw/vfmw_v5.0/firmware/osal/linux_kernel/vfmw_osal.c:// added by huxm 20241209
    	./msp/drv/vfmw/vfmw_v5.0/firmware/osal/linux_kernel/vfmw_osal.c:    #if 0      // added by huxm 20241210
    	./msp/drv/vfmw/vfmw_v5.0/firmware/osal/linux_kernel/vfmw_osal.c:    #if 0      // added by huxm 20241210
    	./msp/drv/vfmw/vfmw_v5.0/firmware/osal/linux_kernel/vfmw_osal.c:    #if 0      // added by huxm 20241210
    	./msp/drv/vfmw/vfmw_v5.0/firmware/osal/linux_kernel/vfmw_osal.c:    #if 0      // added by huxm 20241210
    	./msp/drv/vfmw/vfmw_v4.0/scene/tvp/tvp_adapter.c:   
    					 #if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/vfmw/vfmw_v4.0/scene/tvp/tvp_adapter.c:       
    					 #if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)              // added by huxm 20241210
    	./msp/drv/vfmw/vfmw_v4.0/scene/tvp/tvp_adapter.c:            
    		kernel_write(*ppFile,(HI_U8 *)(g_SaveStreamMem.VirAddr),Length,&(*ppFile)->f_pos); // added by huxm 20241210
    	./msp/drv/vfmw/vfmw_v4.0/scene/tvp/tvp_adapter.c:        
    					#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/vfmw/vfmw_v4.0/firmware/osal/linux_kernel/vfmw_osal.c:
    											// added by huxm 20241208 from "toolchain path"/linux/time.h
    	./msp/drv/vfmw/vfmw_v4.0/firmware/osal/linux_kernel/vfmw_osal.c:// added by huxm 20241209
    	./msp/drv/vfmw/vfmw_v4.0/firmware/osal/linux_kernel/vfmw_osal.c:// added by huxm 20241209
    	./msp/drv/vfmw/vfmw_v4.0/firmware/osal/linux_kernel/vfmw_osal.c:    
    							#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)        // added by huxm 20241210
    	./msp/drv/vfmw/vfmw_v4.0/firmware/osal/linux_kernel/vfmw_osal.c:    
    							#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)          // added by huxm 20241210
    	./msp/drv/vfmw/vfmw_v4.0/firmware/osal/linux_kernel/vfmw_osal.c:        
    								readlen = kernel_read(filp, buf, len, &filp->f_pos);    // added by huxm 20241210
    	./msp/drv/vfmw/vfmw_v4.0/firmware/osal/linux_kernel/vfmw_osal.c:    
    							#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)        // added by huxm 20241210
    	./msp/drv/vfmw/vfmw_v4.0/firmware/osal/linux_kernel/vfmw_osal.c:    
    						#if LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/vfmw/vfmw_v4.0/firmware/osal/linux_kernel/vfmw_osal.c:    
    						#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)              // added by huxm 20241210
    	./msp/drv/vfmw/vfmw_v4.0/firmware/osal/linux_kernel/vfmw_osal.c:        
    							writelen = kernel_write(filp, buf, len, &filp->f_pos);      // added by huxm 20241210
    	./msp/drv/vfmw/vfmw_v4.0/firmware/osal/linux_kernel/vfmw_osal.c:    
    						#elif LINUX_VERSION_CODE <= KERNEL_VERSION(3, 18, 0)            // added by huxm 20241210
    	./msp/drv/vfmw/vfmw_v4.0/firmware/osal/linux_kernel/vfmw_osal.c:    #if 0  // added by huxm 20241209
    	./msp/drv/vfmw/vfmw_v4.0/firmware/osal/linux_kernel/vfmw_osal.c:    #if 0       // added by huxm 20241209
    	./msp/drv/vfmw/vfmw_v4.0/firmware/osal/linux_kernel/vfmw_proc.c:    // added (struct proc_ops *) by huxm 20241209
    	./msp/drv/sync/drv_sync_intf.c:    #if 0   // added by huxm 20241210
    	./msp/drv/sync/drv_sync_intf.c:    #if 0   // added by huxm 20241210
    	./msp/drv/sync/drv_sync.c:// added by huxm 20241209
    	./msp/drv/ir/ir_s2/drv_ir_nec.c:        #if 0                   // delete by huxm 20241218
    	./msp/drv/ir/ir_s2/drv_ir_nec.c:        #else                   // added by huxm 20241218
    	./msp/drv/ir/ir_s2/drv_ir_nec.c:        //nec_timer[i].data = (unsigned long)~0;  // delect by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_nec.c:        
    							nec_timer[i].function = (void *)nec_keyup_proc;     // added (void *) by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_nec.c:        //nec_timer[idx].data = idx;      // delect by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_nec.c:        //nec_timer[idx].data = idx;  // delect by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_nec.c:        //nec_timer[idx].data = idx;  // delect by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_nec.c:        //nec_timer[idx].data = idx;    // delect by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_rc5.c:        #if 0                   // delete by huxm 20241218
    	./msp/drv/ir/ir_s2/drv_ir_rc5.c:        #else                   // added by huxm 20241218
    	./msp/drv/ir/ir_s2/drv_ir_rc5.c:        //rc5_timer[i].data = (unsigned long)~0;    // delect by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_rc5.c:        
    						rc5_timer[i].function = (void *)rc5_keyup_proc;     // added (void *) by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_rc5.c:        //rc5_timer[ip->priv].data = ip->priv;    // delect by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_rc5.c:        //rc5_timer[ip->priv].data = ip->priv;        // delect by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_sony.c:        #if 0                  // delete by huxm 20241218
    	./msp/drv/ir/ir_s2/drv_ir_sony.c:        #else                  // added by huxm 20241218
    	./msp/drv/ir/ir_s2/drv_ir_sony.c:        
    						//sony_timer[i].data = (unsigned long)~0;               // delect by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_sony.c:       
    					 sony_timer[i].function = (void *)sony_keyup_proc;       // added (void *) by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_sony.c:        //sony_timer[idx].data = idx;     // delect by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:    
    						timer_setup(&ir->symbol_timer,NULL,0);                      // added by huxm 20241218
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:    
    					ir->symbol_timer.function = (void *)ir_symbol_timer_proc;   // added (void *) by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:    init_timer(&ir->symbol_timer);              // delete by huxm 20241218
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:    ir->symbol_timer.data = (unsigned long)ir;  // delect by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_tc9012.c:        #if 0                        // delete by huxm 20241218
    	./msp/drv/ir/ir_s2/drv_ir_tc9012.c:        #else                        // added by huxm 20241218
    	./msp/drv/ir/ir_s2/drv_ir_tc9012.c:        
    							//tc9012_timer[i].data = (unsigned long)~0;             // delect by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_tc9012.c:       
    						 tc9012_timer[i].function =(void *)tc9012_keyup_proc;    // added (void *) by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_tc9012.c:        //tc9012_timer[idx].data = idx;     // delect by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_rc6.c:        #if 0                   // delete by huxm 20241218
    	./msp/drv/ir/ir_s2/drv_ir_rc6.c:        #else                   // added by huxm 20241218
    	./msp/drv/ir/ir_s2/drv_ir_rc6.c:        //rc6_timer[i].data = (unsigned long)~0;    // delect by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_rc6.c:        
    							rc6_timer[i].function = (void *)rc6_keyup_proc;     // added (void *) by huxm 20241208
    	./msp/drv/ir/ir_s2/drv_ir_rc6.c:        //rc6_timer[ip->priv].data = ip->priv;    // delect by huxm 20241208
    	./common/drv/userproc/drv_userproc.c:#if 0   // modify by huxm 20241208
    	./common/drv/userproc/drv_userproc.c:    #if 0   // modify by huxm 20241208
    	./common/drv/userproc/drv_userproc.c:    #if 0   // modify by huxm 20241208
    	./common/drv/userproc/drv_userproc.c:    #if 0   // modify by huxm 20241208
    	./common/drv/userproc/drv_userproc.c:    #if 0   // modify by huxm 20241208
    	./common/drv/userproc/drv_userproc.c:    // added (struct proc_ops *) by huxm 20241208
    	./common/drv/userproc/drv_userproc.c:    #if 0   // modify by huxm 20241208
    	./common/drv/file/drv_file_ext.c:    #if 0       //  modify by huxm 20241208
    	./common/drv/file/drv_file_ext.c:    #if 0       //  modify by huxm 20241208
    	./common/drv/file/drv_file_ext.c:    set_fs(KERNEL_DS);  //  modify by huxm 20241208
    	./common/drv/file/drv_file_ext.c:    force_uaccess_end(KERNEL_DS);  //  modify by huxm 20241208
    	./common/drv/file/drv_file_ext.c:    #if 0       //  modify by huxm 20241208
    	./common/drv/file/drv_file_ext.c:    #if 0       //  modify by huxm 20241208
    	./common/drv/file/drv_file_ext.c:       #if 0       //  modify by huxm 20241208
    	./common/drv/stat/drv_stat_ext_k.c:// added by huxm 20241205
    	./common/drv/stat/drv_stat_ext.c:// added by huxm 20241208 from "toolchain path"/linux/time.h
    	./common/drv/stat/drv_stat_ext.c:    
    						#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)           // added by huxm 20241208
    	./common/drv/stat/drv_stat_ext.c: return (long)HI_DRV_UserCopy(file->f_path.dentry->d_inode, 
    												file, cmd, arg, CMPI_STAT_Ioctl);    // added by huxm 20241208
    	./common/drv/stat/drv_stat_ext.c:    #else                                              // added by huxm 20241208
    	./common/drv/stat/drv_stat_ext.c:    #endif                                            // added by huxm 20241208
    	./common/drv/stat/drv_stat_ext.c:// added by huxm 20241208
    	./common/drv/mmz/drv_mmz_userdev.c:#include <linux/mmap_lock.h>         // added by huxm 20241205
    	./common/drv/mmz/drv_mmz_userdev.c:     
    								#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20241205
    	./common/drv/mmz/drv_mmz_userdev.c:     #else                                            // added by huxm 20241205
    	./common/drv/mmz/drv_mmz_userdev.c:     #endif                                          // added by huxm 20241205
    	./common/drv/mmz/drv_mmz_userdev.c:     // added by huxm 20241205
    	./common/drv/mmz/drv_mmz_userdev.c:     // end of added by huxm 20241205
    	./common/drv/mmz/drv_mmz_userdev.c:     #endif  // added by huxm 20241205
    	./common/drv/mmz/drv_mmz_userdev.c:             // added by huxm 20241205
    	./common/drv/mmz/drv_mmz_userdev.c:             // end of added by huxm 20241205
    	./common/drv/mmz/drv_mmz_userdev.c:             #endif  // added by huxm 20241205
    	./common/drv/mmz/drv_mmz_userdev.c:             
    					#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)        // added by huxm 20241205
    	./common/drv/mmz/drv_mmz_userdev.c:             
    						ret = mmz_userdev_ioctl_m(file_inode(file),file, cmd, &mi);    // added by huxm 20241205
    	./common/drv/mmz/drv_mmz_userdev.c:             #else                                // added by huxm 20241205
    	./common/drv/mmz/drv_mmz_userdev.c:             #endif                              // added by huxm 20241205
    	./common/drv/mmz/drv_mmz_userdev.c:             
    							#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)       // added by huxm 20241205
    	./common/drv/mmz/drv_mmz_userdev.c:  ret = mmz_userdev_ioctl_m(file_inode(file),file, 
    												cmd, (struct mmb_info *)&si);       // added by huxm 20241205
    	./common/drv/mmz/drv_mmz_userdev.c:             #else                                 // added by huxm 20241205
    	./common/drv/mmz/drv_mmz_userdev.c:// added by huxm 20241205
    	./common/drv/mmz/drv_mmz_userdev.c:// end of // added by huxm 20241205
    	./common/drv/mmz/drv_mmz_userdev.c:#endif       // added by huxm 20241205
    	./common/drv/himedia/himedia_base.c:#if 0       // delete by huxm 20241205
    	./common/drv/himedia/himedia_base.c://  .dev_attrs      = himedia_dev_attrs,         // delete by huxm 20241205
    	./common/drv/himedia/himedia.c: #if 0   // modify by huxm 20241205
    	./common/drv/proc/drv_proc_ext.c:    // added (struct proc_ops *) by huxm 20241208
    	./common/drv/proc/drv_proc_ext_k.c:        
    								#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20241206
    	./common/drv/proc/drv_proc_ext_k.c:        
    								mm_segment_t stOld_FS = force_uaccess_begin();          // added by huxm 20241206
    	./common/drv/proc/drv_proc_ext_k.c:        #else                                        // added by huxm 20241206
    	./common/drv/proc/drv_proc_ext_k.c:        #endif                                        // added by huxm 20241206
    	./common/drv/proc/drv_proc_ext_k.c: #if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)   // added by huxm 20241206
    	./common/drv/proc/drv_proc_ext_k.c:        force_uaccess_end(stOld_FS);                 // added by huxm 20241206
    	./common/drv/proc/drv_proc_ext_k.c:        #else                                        // added by huxm 20241206
    	./common/drv/proc/drv_proc_ext_k.c:        #endif                                      // added by huxm 20241206
    	./common/drv/sys/drv_sys_ext.c:// extern inline void __iomem * 
    						ioremap_nocache(unsigned long offset,unsigned long size);  // added by huxm 20241208
    	./common/drv/sys/drv_sys_ext.c:    #if 0       // modify by huxm 20241208
    	./common/drv/sys/drv_sys_ext_k.c:// added by huxm 20241205
    	./common/drv/sys/drv_sys_ext_k.c:// extern inline void __iomem *ioremap_nocache(
    										unsigned long physaddr, unsigned long size);   // added by huxm 20241206
    	./common/drv/module/drv_module_ext.c:    #if 0       // modify by huxm 20241208
    	./common/drv/log/drv_log_ext.c:    #if 0       // modify by huxm 20241208
    	./common/drv/log/drv_log_ext_k.c:// added by huxm 20241208 from "toolchain path"/linux/time.h
    	./common/include/hi_math.h:#include <linux/kernel.h>   //added by huxm 20241208
    	./common/include/hi_math.h:// added by huxm 20241208 from "toolchain path"/linux/time.h
    	./kernel/linux-5.15.134/fs/seq_file.c:
    						//void seq_printf(struct seq_file *m, const char *f, ...)      // delete by huxm 20241216
    	./kernel/linux-5.15.134/fs/seq_file.c:
    							int seq_printf(struct seq_file *m, const char *f, ...)       // added by huxm 20241216
    	./kernel/linux-5.15.134/fs/seq_file.c:  return 1;                                       // added by huxm 20241216
    	./kernel/linux-5.15.134/arch/arm/tools/mach-types:# added by huxm 20241205
    	./kernel/linux-5.15.134/arch/arm/Makefile:# added by huxm 20240102
    	./kernel/linux-5.15.134/arch/arm/Makefile:#added by huxm 20240102
    	./kernel/linux-5.15.134/arch/arm/boot/compressed/head.S: *  Annotate by huxm 20240108
    	./kernel/linux-5.15.134/include/linux/interrupt.h:#include <linux/linkage.h>  // added by huxm 20241208
    	./kernel/linux-5.15.134/include/linux/interrupt.h:#include <linux/preempt.h>    // added by huxm 20241208
    	./kernel/linux-5.15.134/include/linux/interrupt.h:#define IRQF_DISABLED    0x00000020  // added by huxm 20241208
    	./kernel/linux-5.15.134/include/linux/seq_file.h:#if 0  // delete by huxm 20241216
    	./kernel/linux-5.15.134/include/linux/seq_file.h:#else  // added by huxm 20241216
    	./kernel/linux-5.15.134/include/linux/dma-mapping.h:// added by huxm 20241212
    	./kernel/linux-5.15.134/include/linux/gpio/driver.h:    struct list_head        list;   // added by huxm 20241216
    	./kernel/linux-5.15.134/include/linux/iommu.h:#include <trace/events/iommu.h>         //added by huxm 20241205
    	./kernel/linux-5.15.134/include/linux/iommu.h:#if 1             // added by huxm 20241204
    	./kernel/linux-5.15.134/include/linux/cpufreq.h:// added by huxm 20241217
    	./kernel/linux-5.15.134/include/linux/skbuff.h:// added by huxm 20241211
    	./kernel/linux-5.15.134/drivers/cpufreq/Kconfig: added Hisilicon CPU frequency scaling config by huxm 20241205
    	./kernel/linux-5.15.134/drivers/cpufreq/bmips-cpufreq.c:     
    												added Hisilicon CPU frequency scaling config by huxm 20241205
    	./kernel/linux-5.15.134/drivers/staging/android/Makefile:#added by huxm 20241205
    	./kernel/linux-5.15.134/drivers/staging/android/Kconfig:      added by huxm 20241205
    	./kernel/linux-5.15.134/drivers/staging/android/Kconfig:          added by huxm 20241205
    	./kernel/linux-5.15.134/drivers/staging/android/Kconfig:      added by huxm 20241205
    	./kernel/linux-5.15.134/drivers/staging/android/Kconfig:          added by huxm 20241205
    	./kernel/linux-5.15.134/drivers/staging/android/Kconfig:     added by huxm 20241205
    	./kernel/linux-5.15.134/drivers/staging/android/Kconfig:     added by huxm 20241205
    	./kernel/linux-5.15.134/drivers/staging/android/Kconfig:     added by huxm 20241205
    	./kernel/linux-5.15.134/drivers/staging/android/Kconfig:               added by huxm 20241205
    	./kernel/linux-5.15.134/drivers/staging/android/Kconfig:               added by huxm 20241205
    	./kernel/linux-5.15.134/drivers/staging/android/Kconfig:               added by huxm 20241205
    	./kernel/linux-5.15.134/drivers/staging/android/Kconfig:               added by huxm 20241205
    	./kernel/linux-5.15.134/scripts/Makefile.lib:# cat                      copy from kernel3.x by huxm 20240103
    	./kernel/linux-5.15.134/kernel/time/timekeeping.c:// added by huxm 20241217 from "toolchain path"/linux/time.h
    	./kernel/linux-5.15.134/kernel/time/timekeeping.c:  * added by huxm 20241219 from linux-3.18.y
    
    grep -r -E 'huxm 2025|HUXM_2025' ./
    	./component/exfat/Makefile:#            added by huxm 20250118
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:                       /* added by huxm 20251237  */
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts: clock-accuracy = <100000>;  // added by huxm 20251231
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts: 
    											status = "okay"; // 明确确保控制器启用 added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:  
    											clock-accuracy = <100000>;    // added by huxm 20251231
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts: 
    											status = "okay"; // 明确确保控制器启用 added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:   
    											clock-accuracy = <100000>;    // added by huxm 20251231
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts: 
    											status = "okay"; // 明确确保控制器启用 added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts: //    <0xf8a02000 0x100>;   // deleted by huxm 20251227
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts: <0xf8a02000 0x1000>;       // added by huxm 20251227
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts: 
    												status = "okay"; // 明确确保控制器启用 added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:  #clock-cells = <1>;          // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:   status = "okay"; // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:   #clock-cells = <1>;       // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:     status = "okay"; // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:    #clock-cells = <1>;      // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:              status = "okay"; // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:   #clock-cells = <1>;       // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:   #clock-cells = <1>;        // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:             status = "okay"; // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:   
    							//reg = <0xF8A22000 0x200>, <0xF8A20000 0x0848>;        // deleted by huxm 20251229
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:  
    								reg = <0xF8A22000 0x1000>, <0xF8A20000 0x0848>;         // added by huxm 20251229
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:                     
    							 //reg = <0xf9810000 0x100>, <0xfe000000 0x2176>;        // deleted by huxm 20251229
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:                  
    						    reg = <0xf9810000 0x1000>, <0xfe000000 0x2176>;         // added by huxm 20251229
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:        
    					              interrupts = <GIC_SPI 32 IRQ_TYPE_LEVEL_HIGH>;     // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:  #clock-cells = <1>;     // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:         // status = "okay"; // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:      status = "okay"; // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:   // #clock-cells = <1>;      // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:         status = "okay"; // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:     // #clock-cells = <1>;  // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:    status = "okay"; // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:    // #clock-cells = <1>;     // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:     status = "okay"; // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:   // #clock-cells = <1>;     // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:    status = "okay"; // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:    // #clock-cells = <1>;    // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:       status = "okay"; // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:    // #clock-cells = <1>;    // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:         status = "okay"; // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:         status = "okay"; // added by huxm 20251228
    	./kernel/linux-5.15.134/arch/arm/mach-hi3798mx/Kconfig:   
    											Support DDR2 and DDR3.added HAVE_ARM_ARCH_TIMER by huxm 20251228
    	./kernel/linux-5.15.134/drivers/mmc/host/Makefile:# added by huxm 20251229
    	./kernel/linux-5.15.134/drivers/mmc/host/himciv200/himciv200.c:
    											#include <linux/interrupt.h>             // added by huxm 20251229
    	./kernel/linux-5.15.134/drivers/mmc/host/himciv200/himciv200.c:
    					#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size)   // added by huxm 20251229
    	./kernel/linux-5.15.134/drivers/mmc/host/himciv200/himciv200.c://       Deleted by huxm 20251229
    	./kernel/linux-5.15.134/drivers/mmc/host/himciv200/himciv200.c:
    						static void himciv200_detect_card(struct timer_list *t)     // Replaced by huxm 20251229
    	./kernel/linux-5.15.134/drivers/mmc/host/himciv200/himciv200.c: 
    			struct himciv200_host *host = from_timer(host, t, timer); // 从t中获取host结构体 Replaced by huxm 20251229
    	./kernel/linux-5.15.134/drivers/mmc/host/himciv200/himciv200.c:         
    							/* linux-5.15内核不再支持流模式，没有MMC_DATA_STREAM这个宏。Deleted by huxm 20251229*/
    	./kernel/linux-5.15.134/drivers/mmc/host/himciv200/himciv200.c: /* deleted by huxm 20251229*/
    	./kernel/linux-5.15.134/drivers/mmc/host/himciv200/himciv200.c:
    												/* 替换旧的 init_timer/add_timer   added by huxm 20251229   */
    	./kernel/linux-5.15.134/drivers/mmc/host/Kconfig:# added by huxm 20251229
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:  clk->state_use_accessors = CLOCK_EVT_MODE_UNUSED;      
    								 // "clk->mode"  ----->  clk->state_use_accessors   modify by huxm 20251218
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:#ifdef CLK2CLK_HW_BY_HUXM_20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:
    					/* ---------------------------------  CLK2CLK_HW_BY_HUXM_20251222  -----------------------*/
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:
    														#ifdef                 CLK2CLK_HW_BY_HUXM_20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c
    		:#else  /* -----------------------------  CLK2CLK_HW_BY_HUXM_20251222  ----------------------------------*/
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:
    		#endif /* -----------------------------  CLK2CLK_HW_BY_HUXM_20251222  ----------------------------------*/
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:
    		/* -------------------------------------  CLK2CLK_HW_BY_HUXM_20251222  ----------------------------------*/
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:
    								#ifdef                 CLK2CLK_HW_BY_HUXM_20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:
    		#else  /* -----------------------------  CLK2CLK_HW_BY_HUXM_20251222  ----------------------------------*/
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:
    		#endif /* -----------------------------  CLK2CLK_HW_BY_HUXM_20251222  ----------------------------------*/
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:
    		/* ------------------------------------  CLK2CLK_HW_BY_HUXM_20251222  ----------------------------------*/
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:
    							#ifdef                 CLK2CLK_HW_BY_HUXM_20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:// added by huxm 20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:// end of added by huxm 20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:
    		#else  /* -----------------------------  CLK2CLK_HW_BY_HUXM_20251222  ----------------------------------*/
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:
    		#endif /* -----------------------------  CLK2CLK_HW_BY_HUXM_20251222  ----------------------------------*/
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:
    		/* ------------------------------------  CLK2CLK_HW_BY_HUXM_20251222  ----------------------------------*/
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:
    				#ifdef                 CLK2CLK_HW_BY_HUXM_20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:// added by huxm 20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:
    		#else  /* -----------------------------  CLK2CLK_HW_BY_HUXM_20251222  ----------------------------------*/
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:
    		#endif /* -----------------------------  CLK2CLK_HW_BY_HUXM_20251222  ----------------------------------*/
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.h:#define CLK2CLK_HW_BY_HUXM_20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.h:#ifndef CLK2CLK_HW_BY_HUXM_20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.h:#ifdef CLK2CLK_HW_BY_HUXM_20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.h:#ifdef CLK2CLK_HW_BY_HUXM_20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.h:#ifndef CLK2CLK_HW_BY_HUXM_20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.h:
    										int hiclk_init(struct clk_hw *hw);     // added by huxm 20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.h:#ifdef CLK2CLK_HW_BY_HUXM_20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.c:#ifdef CLK2CLK_HW_BY_HUXM_20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.c:       #ifdef CLK2CLK_HW_BY_HUXM_20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.c:
    									int hiclk_init(struct clk_hw *hw)      // added by huxm 20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.c:            return 0;       // added by huxm 20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.c:#ifdef CLK2CLK_HW_BY_HUXM_20251222
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.c:#else  
    				/* ======================= CLK2CLK_HW_BY_HUXM_20251222 ======================================= */
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.c:       
    									static int clkdummy_init(struct clk_hw *hw)     // added by huxm 20251222
    
    grep -r -E 'huxm 2026|HUXM_2026' ./
    	./msp/drv/cipher/drv_cipher.c:// added by huxm 20260606
    	./msp/drv/cipher/drv_cipher.c:// end of added by huxm 20260606
    	./msp/drv/cipher/drv_cipher.c:// added by huxm 20260606
    	./msp/drv/cipher/drv_cipher.c:// end of added by huxm 20260606
    	./msp/drv/cipher/drv_cipher.c:    HI_S32 v_irq;               // added by huxm 20260606
    	./msp/drv/cipher/drv_cipher.c:    // added by huxm 20260606
    	./msp/drv/cipher/drv_cipher.c:    // end of added by huxm 20260606
    	./msp/drv/cipher/drv_cipher.c:    #endif  
    						// #if (LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0))   added by huxm 20260606
    	./msp/drv/cipher/hal_cipher.c:
    					#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size)      //added by huxm 20260531
    	./msp/drv/cipher/drv_cipher_intf.c:
    					#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size)      //added by huxm 20260531
    	./msp/drv/cipher/drv_cipher_intf.c:    hiCipher_module_init();     // added by huxm 20260606
    	./msp/drv/cipher/drv_cipher_intf.c:    hiCipher_module_exit();     // added by huxm 20260606
    	./msp/drv/pq/pq_v3_0/drv_pq.c:    /* deleted by huxm 20260117
    	./msp/drv/pq/pq_v3_0/drv_pq.c:    
    			PROC_PRINT(s, "%-20s: %s \n", "Driver version", "PQ_V3_0"PQ_MODIFY_TIME);   // added by huxm 20260117
    	./msp/drv/venc/venc_v1.0/drv_venc.c:    #ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc.c:        #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc.c:        #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc.c:    #ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_omxvenc.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_omxvenc.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_omxvenc.c:        #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_omxvenc.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_osal.c:#include <linux/version.h>      // added by huxm 20260606
    	./msp/drv/venc/venc_v1.0/drv_venc_proc.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_proc.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_proc.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_proc.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_proc.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_proc.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_omxvenc_efl.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_omxvenc_efl.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_omxvenc_efl.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_omxvenc_efl.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_omxvenc_efl.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_omxvenc_efl.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_omxvenc_efl.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_omxvenc_efl.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_omxvenc_efl.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_omxvenc_efl.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_omxvenc_efl.c:    #ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_omxvenc_efl.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_omxvenc_efl.c:    #ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_omxvenc_efl.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_omxvenc_efl.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:    #ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:        #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/venc/venc_v1.0/drv_venc_efl.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vi/drv_vi_proc.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vi/drv_vi_proc.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vi/drv_vi_proc.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vi/drv_vi.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vi/drv_vi.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vi/drv_vi.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vi/drv_vi.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vi/drv_vi.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/advca/drv_advca_intf.c:
    					#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size)      //added by huxm 20260531
    	./msp/drv/advca/V300/drv_advca_v300.c:
    					#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size)      //added by huxm 20260531
    	./msp/drv/advca/drv_advca_common.c:
    					#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size)      //added by huxm 20260531
    	./msp/drv/adec/adec_v1_1/drv_adec.c:#include <linux/timekeeping.h>      // added by huxm 20260531
    	./msp/drv/adec/adec_v1_1/drv_adec.c:#define get_seconds ktime_get_seconds      // added by huxm 20260531
    	./msp/drv/pm/opp.c:/* deleted __init by huxm 20260118
    	./msp/drv/pm/opp.c:    replaced by huxm 20260118      */
    	./msp/drv/pm/hi_opp_data.c:/*   deleted __init by huxm 20260118
    	./msp/drv/pm/hi_opp_data.c:     replaced by huxm 20260118   */
    	./msp/drv/pm/drv_pmoc_intf.c:
    				#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size)      //added by huxm 20260531
    	./msp/drv/pm/hi_cpufreq.c:    #if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)   // added by huxm 20260531
    	./msp/drv/pm/hi_cpufreq.c:    cpus_read_lock();                                   // added by huxm 20260531
    	./msp/drv/pm/hi_cpufreq.c:    #else                                               // added by huxm 20260531
    	./msp/drv/pm/hi_cpufreq.c:    #endif                                              // added by huxm 20260531
    	./msp/drv/pm/hi_cpufreq.c:    #if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)     // added by huxm 20260531
    	./msp/drv/pm/hi_cpufreq.c:    cpus_read_unlock();     // added by huxm 20260531
    	./msp/drv/pm/hi_cpufreq.c:    #else                   // added by huxm 20260531
    	./msp/drv/pm/hi_cpufreq.c:    #endif                  // added by huxm 20260531
    	./msp/drv/pm/hi_cpufreq.c:    // unsigned int i;     // deleted by huxm 20260602
    	./msp/drv/pm/hi_cpufreq.c:    unsigned int i = 0;     // added by huxm 20260602
    	./msp/drv/pm/hi_cpufreq.c:#define strnicmp strncasecmp    // added by huxm 20260531
    	./msp/drv/pm/hi_cpufreq.c:    // return;         // deleted by huxm 20260602
    	./msp/drv/pm/hi_cpufreq.c:    // added by huxm 20260622
    	./msp/drv/pm/hi_cpufreq.c:    // end of added by huxm 20260622
    	./msp/drv/pm/hi_cpufreq.c:    #else           // added by huxm 20260622
    	./msp/drv/pm/hi_cpufreq.c:    #endif          // added by huxm 20260622
    	./msp/drv/pm/hi_cpufreq.c:        max_freq = max(freq_table[i].frequency, max_freq);  // deleted by huxm 20260602
    	./msp/drv/pm/hi_cpufreq.c:        
    							// if (freq_table[i].frequency > max_freq)                // replaced by huxm 20260602
    	./msp/drv/pm/hi_cpufreq.c:   // max_freq = freq_table[i].frequency;                // replaced by huxm 20260602
    	./msp/drv/pm/hi_cpufreq.c:/*   deleted __init by huxm 20260118
    	./msp/drv/pm/hi_cpufreq.c:     replaced by huxm 20260118   */
    	./msp/drv/pm/hi_cpufreq.c:        hi_cpufreq_boost_init_or_exit(1);   // added by huxm 20260622
    	./msp/drv/pm/hi_cpufreq.c:    hi_cpufreq_boost_init_or_exit(1);   // added by huxm 20260622
    	./msp/drv/otp/drv_otp_common.c:
    					#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size)      //added by huxm 20260531
    	./msp/drv/jpge/src/jpge_osr.c:    hiJPGE_module_exit();           // added by huxm 20260606
    	./msp/drv/jpge/src/jpge_osr.c:    hiJPGE_module_init();           // added by huxm 20260606
    	./msp/drv/jpge/src/jpge_hal.c:// added by huxm 20260606
    	./msp/drv/jpge/src/jpge_hal.c:// end of added by huxm 20260606
    	./msp/drv/jpge/src/jpge_hal.c:// added by huxm 20260606
    	./msp/drv/jpge/src/jpge_hal.c:// end of added by huxm 20260606
    	./msp/drv/jpge/src/jpge_hal.c:    HI_S32 v_irq;                                       // added by huxm 20260606
    	./msp/drv/jpge/src/jpge_hal.c:    // added by huxm 20260606
    	./msp/drv/jpge/src/jpge_hal.c:    // end of added by huxm 20260606
    	./msp/drv/jpge/src/jpge_hal.c:    #endif  
    								// #if (LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0))  added by huxm 20260606
    	./msp/drv/jpge/src/jpge_osal.c:// added by huxm 20260606
    	./msp/drv/jpge/src/jpge_osal.c:// end of added by huxm 20260606
    	./msp/drv/jpge/src/jpge_osal.c:#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)  // added by huxm 20260606
    	./msp/drv/gpu/mali4xx/linux/mali_memory_secure.c:#include <linux/dma-direct.h>  // added by huxm 20260529
    	./msp/drv/gpu/mali4xx/linux/mali_linux_trace.h:  // #define TRACE_INCLUDE_PATH .   // deleted by huxm 20260530
    	./msp/drv/gpu/mali4xx/linux/mali_linux_trace.h:
    					#define TRACE_INCLUDE_PATH ../../../../msp/drv/gpu/mali4xx/linux // replaced by huxm 20260530
    	./msp/drv/gpu/mali4xx/linux/mali_osk_low_level_mem.c:
    					#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size)      //added by huxm 20260531
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_linux.c:// added by huxm 20260606
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_linux.c:// end of added by huxm 20260606
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_linux.c:#if defined(CONFIG_TRACEPOINTS)         // added by huxm 20260530
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_linux.c:// added by huxm 20260606
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_linux.c:// end of added by huxm 20260606
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_linux.c:        // added by huxm 20260606
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_linux.c:        // end of added by huxm 20260606
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_linux.c:        #endif  // added by huxm 20260606
    	./msp/drv/gpu/mali4xx/linux/mali_kernel_linux.c:    hiGPU_AUX_hwirq_remap_virq(pdev);   // added by huxm 20260606
    	./msp/drv/gpu/mali4xx/linux/mali_osk_profiling.c:#if !defined(CONFIG_TRACEPOINTS)       // added by huxm 20260530
    	./msp/drv/gpu/mali4xx/linux/mali_osk_profiling.c:
    				void _mali_osk_profiling_record_global_counters(int counter_id, u32 value);// added by huxm 20260530
    	./msp/drv/gpu/mali4xx/linux/mali_osk_profiling.c:#if defined(CONFIG_TRACEPOINTS)        // added by huxm 20260530
    	./msp/drv/gpu/mali4xx/linux/mali_osk_profiling.c:#if defined(CONFIG_TRACEPOINTS)        // added by huxm 20260530
    	./msp/drv/gpu/mali4xx/linux/mali_osk_profiling.c:       
    											#if defined(CONFIG_TRACEPOINTS)         // added by huxm 20260530
    	./msp/drv/gpu/mali4xx/linux/mali_osk_profiling.h:#include <linux/version.h>      // added by huxm 20260530
    	./msp/drv/gpu/mali4xx/linux/mali_osk_profiling.h:
    									#if LINUX_VERSION_CODE < KERNEL_VERSION(5,15,0)  // added by huxm 20260531
    	./msp/drv/gpu/mali4xx/linux/mali_osk_profiling.h:#endif      // added by huxm 20260531
    	./msp/drv/gpu/mali4xx/linux/mali_memory_cow.c:
    					#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size)      //added by huxm 20260531
    	./msp/drv/gpu/mali4xx/common/mali_group.c:#include "mali_utgard_profiling_events.h"     // added by huxm 20260529
    	./msp/drv/gpu/mali4xx/common/mali_group.c:#include "../linux/mali_linux_trace.h"        // added by huxm 20260529
    	./msp/drv/gpu/mali4xx/common/mali_group.c:// added by huxm 20260529
    	./msp/drv/gpu/mali4xx/platform/mali400/mali4xx_clk.c:/*   deleted __init by huxm 20260118
    	./msp/drv/gpu/mali4xx/platform/mali400/mali4xx_clk.c:     replaced by by huxm 20260118   */
    	./msp/drv/gpu/mali4xx/platform/mali400/mali4xx_pmu.c:/*   deleted __init by huxm 20260118
    	./msp/drv/gpu/mali4xx/platform/mali400/mali4xx_pmu.c:     replaced by huxm 20260118   */
    	./msp/drv/gpu/mali4xx/platform/mali400/mali4xx.c:#include <linux/pm_runtime.h>       // added by huxm 20260531
    	./msp/drv/gpu/mali4xx/platform/arm/arm.c:#include <linux/pm_runtime.h>       // added by huxm 20260531
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx_clk.c:/*   deleted __init by huxm 20260118
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx_clk.c:     replaced by by huxm 20260118   */
    	./msp/drv/gpu/mali4xx/platform/mali450/mali4xx.c:#include <linux/pm_runtime.h>       // added by huxm 20260531
    	./msp/drv/adsp/adsp_v1_1/Makefile:# added by huxm 20260611
    	./msp/drv/adsp/adsp_v1_1/Makefile:# end of added by huxm 20260611
    	./msp/drv/adsp/adsp_v1_1/drv_adsp.c:#include "external/ASRC_ARM/inc/imedia_asrc_api.h" //added by huxm 20260531
    	./msp/drv/adsp/adsp_v1_1/drv_adsp.c:
    						#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size) //added by huxm 20260531
    	./msp/drv/adsp/adsp_v1_1/osal/adsp_osal.c:
    						#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size)  //added by huxm 20260531
    	./msp/drv/demux/demux_v2/drv_demux_intf.c:// added by huxm 20260606
    	./msp/drv/demux/demux_v2/drv_demux_intf.c:// end of added by huxm 20260606
    	./msp/drv/demux/demux_v2/drv_demux_intf.c:// added by huxm 20260606
    	./msp/drv/demux/demux_v2/drv_demux_intf.c:// end of added by huxm 20260606
    	./msp/drv/demux/demux_v2/drv_demux.c:#include <linux/timekeeping.h>      // added by huxm 20260531
    	./msp/drv/demux/demux_v2/drv_demux.c:#define get_seconds ktime_get_seconds      // added by huxm 20260531
    	./msp/drv/demux/demux_v2/drv_demux_func.c:// added by huxm 20260606
    	./msp/drv/demux/demux_v2/drv_demux_func.c:// end of added by huxm 20260606
    	./msp/drv/demux/demux_v2/drv_demux_func.c:
    					#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size)      //added by huxm 20260531
    	./msp/drv/demux/demux_v2/drv_demux_func.c:// added by huxm 20260606
    	./msp/drv/demux/demux_v2/drv_demux_func.c:// end of added by huxm 20260606
    	./msp/drv/demux/demux_v2/drv_demux_func.c:
    								#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20260606
    	./msp/drv/demux/demux_v2/drv_demux_func.c:#else                                // end of added by huxm 20260606
    	./msp/drv/frontend/drv_tuner.c:#include <linux/timekeeping.h>      // added by huxm 20260531
    	./msp/drv/frontend/drv_tuner.c:#define get_seconds ktime_get_seconds      // added by huxm 20260531
    	./msp/drv/keyled/keyled_std/drv_keyled_std.c:
    					#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size)      //added by huxm 20260531
    	./msp/drv/keyled/keyled_ct1642/drv_keyled_ct1642_inner.c:
    					#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size)      //added by huxm 20260531
    	./msp/drv/gpio/drv_gpio.c:#include <linux/gpio.h>     // added by huxm 20260531
    	./msp/drv/gpio/drv_gpio.c:#include <linux/version.h>  // added by huxm 20260531
    	./msp/drv/gpio/drv_gpio.c:#include <linux/device.h>   // added by huxm 20260531
    	./msp/drv/gpio/drv_gpio.c:    #if LINUX_VERSION_CODE < KERNEL_VERSION(5, 15, 0)       // added by huxm 20260531
    	./msp/drv/gpio/drv_gpio.c:    #endif                                                  // added by huxm 20260531
    	./msp/drv/gpio/drv_gpio.c:    // added by huxm 20260531
    	./msp/drv/gpio/drv_gpio.c:    // end of added by huxm 20260531
    	./msp/drv/gpio/drv_gpio.c:    #endif  // added by huxm 20260531
    	./msp/drv/vo/vdp_v3_0/com/drv_disp_debug.c:#include <linux/timekeeping.h>      // added by huxm 20260531
    	./msp/drv/vo/vdp_v3_0/com/drv_disp_debug.c:#define get_seconds ktime_get_seconds      // added by huxm 20260531
    	./msp/drv/vo/Makefile:# deleted by huxm 20260612
    	./msp/drv/vo/Makefile:# replaced by huxm 20260612
    	./msp/drv/vo/vdp_v2_0/drv_disp_intf.c:// added by huxm 20260606
    	./msp/drv/vo/vdp_v2_0/drv_disp_intf.c:// end of added by huxm 20260606
    	./msp/drv/vo/vdp_v2_0/drv_disp_intf.c:    // added by huxm 20260606
    	./msp/drv/vo/vdp_v2_0/drv_disp_intf.c:    // end of added by huxm 20260606
    	./msp/drv/vo/vdp_v2_0/drv_disp_intf.c:    // added by huxm 20260606
    	./msp/drv/vo/vdp_v2_0/drv_disp_intf.c:    // end of added by huxm 20260606
    	./msp/drv/vo/vdp_v2_0/drv/drv_virtual.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_virtual.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_virtual.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_disp_cast.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_disp_cast.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_disp_cast.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_disp_cast.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_disp_cast.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_disp_cast.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_disp_cast.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_disp_cast.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_disp_cast.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_disp_cast.c:        #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_disp_cast.c:        #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_disp_cast.c:        #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_disp_cast.c:        #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_disp_cast.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_window.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_window.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_window.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_window.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_window.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_window.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_window.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_window.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_window.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_window.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv/drv_window.c:                    fallthrough;        // added by huxm 20260118
    	./msp/drv/vo/vdp_v2_0/drv/drv_display.c:// added by huxm 20260606
    	./msp/drv/vo/vdp_v2_0/drv/drv_display.c:// end of added by huxm 20260606
    	./msp/drv/vo/vdp_v2_0/drv/drv_display.c:// added by huxm 20260606
    	./msp/drv/vo/vdp_v2_0/drv/drv_display.c:// end of added by huxm 20260606
    	./msp/drv/vo/vdp_v2_0/drv/drv_display.c:    HI_S32 v_irq;                         // added by huxm 20260606
    	./msp/drv/vo/vdp_v2_0/drv/drv_display.c:    // added by huxm 20260606
    	./msp/drv/vo/vdp_v2_0/drv/drv_display.c:    // end of added by huxm 20260606
    	./msp/drv/vo/vdp_v2_0/drv/drv_display.c:    #endif  // #ifdef __IS_KO_MODULE__  added by huxm 20260606
    	./msp/drv/vo/vdp_v2_0/com/drv_disp_debug.c:#include <linux/timekeeping.h>      // added by huxm 20260531
    	./msp/drv/vo/vdp_v2_0/com/drv_disp_debug.c:#define get_seconds ktime_get_seconds      // added by huxm 20260531
    	./msp/drv/vo/vdp_v2_0/drv_disp_adp2unf.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_disp_adp2unf.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_disp_adp2unf.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_disp_adp2unf.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_disp_adp2unf.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_disp_adp2unf.c:     #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_disp_adp2unf.c:     #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_disp_adp2unf.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/alg/drv_disp_alg_service.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/alg/drv_disp_alg_service.c: #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_disp.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_disp.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_disp.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_disp.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/drv_win.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vo/vdp_v2_0/hal/3798m/vdp_driver.c:                #ifdef fallthrough      // added by huxm 20260118
    	./msp/drv/vo/vdp_v2_0/hal/3798m/vdp_driver.c:                #ifdef fallthrough      // added by huxm 20260118
    	./msp/drv/hdmi/hdmi_1_4/hdmi_intf.c:        #ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/hdmi/hdmi_1_4/hdmi_intf.c:        #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/omxvdec/omxvdec_v1.0/processor_vpss.c:// #define ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/omxvdec/omxvdec_v1.0/processor_vpss.c:    #ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/omxvdec/omxvdec_v1.0/processor_vpss.c: #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/omxvdec/omxvdec_v1.0/processor_vpss.c: #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/omxvdec/omxvdec_v1.0/processor_vpss.c: #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/omxvdec/omxvdec_v1.0/omxvdec.c:    #ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/omxvdec/omxvdec_v1.0/omxvdec.c:    #ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/omxvdec/omxvdec_v1.0/omxvdec.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/omxvdec/omxvdec_v1.0/omxvdec.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/omxvdec/omxvdec_v1.0/omxvdec.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/tde/src/tde_osr.c:// added by huxm 20260606
    	./msp/drv/tde/src/tde_osr.c:// end of added by huxm 20260606
    	./msp/drv/tde/src/tde_osr.c:// added by huxm 20260606
    	./msp/drv/tde/src/tde_osr.c:// end of added by huxm 20260606
    	./msp/drv/tde/src/tde_osr_k.c:// added by huxm 20260606
    	./msp/drv/tde/src/tde_osr_k.c:// end of added by huxm 20260606
    	./msp/drv/tde/src/tde_osr_k.c:// added by huxm 20260606
    	./msp/drv/tde/src/tde_osr_k.c:#else   // end of added by huxm 20260606
    	./msp/drv/tde/src/tde_osr_k.c:// added by huxm 20260606
    	./msp/drv/tde/src/tde_osr_k.c:// end of added by huxm 20260606
    	./msp/drv/tde/src/tde_osr_k.c:    HI_S32 v_irq;                                    // added by huxm 20260606
    	./msp/drv/tde/src/tde_osr_k.c:    // added by huxm 20260606
    	./msp/drv/tde/src/tde_osr_k.c:    // end of added by huxm 20260606
    	./msp/drv/tde/src/tde_osr_k.c:    #endif  // #if LINUX_VERSION_CODE  added by huxm 20260606
    	./msp/drv/tde/adp/tde_v1_0/tde_osictl_k.c:// #define ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/tde/adp/tde_v1_0/tde_osictl_k.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/tde/adp/tde_v1_0/tde_osictl_k.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/tde/adp/tde_v1_0/tde_osictl_k.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/tde/adp/tde_v1_0/tde_osictl_k.c:     #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/tde/adp/tde_v1_0/tde_osictl_k.c:     #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/tde/adp/tde_v1_0/tde_osictl_k.c:     #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/tde/adp/tde_v1_0/tde_osictl_k.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/tde/adp/tde_v1_0/tde_osictl_k.c:     #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/tde/adp/tde_v1_0/tde_osictl_k.c:      #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/tde/adp/tde_v1_0/tde_osictl_k.c:       #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/tde/adp/tde_v1_0/tde_osictl_k.c:       #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/tde/adp/tde_v1_0/tde_osictl_k.c:       #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/tde/adp/tde_v1_0/tde_osictl_k.c:        #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/tde/adp/tde_v1_0/tde_osictl_k.c:        #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/tde/adp/tde_v1_0/tde_osictl_k.c:        #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/tde/adp/tde_v1_0/tde_osictl_k.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/tde/adp/tde_v1_0/tde_osictl_k.c:        #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/tde/adp/tde_v1_0/tde_osictl_k.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vpss/vpss_v3_0/drv_vpss_intf_k.c:// added by huxm 20260606
    	./msp/drv/vpss/vpss_v3_0/drv_vpss_intf_k.c:// end of added by huxm 20260606
    	./msp/drv/vpss/vpss_v3_0/drv_vpss_intf_k.c:// added by huxm 20260606
    	./msp/drv/vpss/vpss_v3_0/drv_vpss_intf_k.c:// end of added by huxm 20260606
    	./msp/drv/vpss/vpss_v3_0/vpss_ctrl.c:// added by huxm 20260606
    	./msp/drv/vpss/vpss_v3_0/vpss_ctrl.c:// end of added by huxm 20260606
    	./msp/drv/vpss/vpss_v3_0/vpss_ctrl.c:// added by huxm 20260606
    	./msp/drv/vpss/vpss_v3_0/vpss_ctrl.c:// end of added by huxm 20260606
    	./msp/drv/vpss/vpss_v3_0/vpss_ctrl.c:    // added by huxm 20260606
    	./msp/drv/vpss/vpss_v3_0/vpss_ctrl.c:    #endif  // #if LINUX_VERSION_CODE  added by huxm 20260606
    	./msp/drv/vpss/vpss_v3_0/vpss_ctrl.c:    // end of added by huxm 20260606
    	./msp/drv/vpss/vpss_v3_0/vpss_ctrl.c:    #if LINUX_VERSION_CODE < KERNEL_VERSION(5,15,0)// added by huxm 20260531
    	./msp/drv/vpss/vpss_v3_0/vpss_ctrl.c:    #if LINUX_VERSION_CODE < KERNEL_VERSION(5,15,0)// added by huxm 20260531
    	./msp/drv/vpss/vpss_v3_0/vpss_ctrl.c:    #endif  // added by huxm 20260531
    	./msp/drv/vpss/vpss_v3_0/vpss_in/hi3798mv100/vpss_in_3798mv100.c:
    								#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vpss/vpss_v3_0/vpss_in/hi3798mv100/vpss_in_3798mv100.c:
    								#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vpss/vpss_v3_0/vpss_in/hi3798mv100/vpss_in_3798mv100.c:    
    								#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vpss/vpss_v3_0/vpss_in/hi3798mv100/vpss_in_3798mv100.c:    
    								#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vpss/vpss_v3_0/vpss_in/hi3798mv100/vpss_in_3798mv100.c:    
    								#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vpss/vpss_v3_0/vpss_in/hi3798mv100/vpss_in_3798mv100.c:    
    								#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vpss/vpss_v3_0/vpss_in/hi3798mv100/vpss_in_3798mv100.c:   
    								 #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vpss/vpss_v3_0/vpss_in/hi3798mv100/vpss_in_3798mv100.c:   
    								 #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vpss/vpss_v3_0/vpss_in/hi3798mv100/vpss_in_3798mv100.c:   
    								 #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vpss/vpss_v3_0/vpss_in/hi3798mv100/vpss_in_3798mv100.c:   
    								 #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vpss/vpss_v3_0/vpss_osal.c:#include <linux/timekeeping.h>      // added by huxm 20260531
    	./msp/drv/vpss/vpss_v3_0/vpss_osal.c:#define get_seconds ktime_get_seconds      // added by huxm 20260531
    	./msp/drv/vpss/vpss_v3_0/vpss_instance.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vpss/vpss_v3_0/vpss_instance.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vpss/vpss_v3_0/vpss_instance.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vpss/vpss_v3_0/vpss_instance.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vpss/vpss_v3_0/hal/hi3798mv100/vpss_hal_3798m.c:        fallthrough;        // added by huxm 20260118
    	./msp/drv/vpss/vpss_v3_0/hal/hi3798mv100/vpss_hal_3798m.c:        fallthrough;        // added by huxm 20260118
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:// added by huxm 20260606
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:// end of added by huxm 20260606
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:// added by huxm 20260606
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:// end of added by huxm 20260606
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:    HI_S32 v_irq;       // added by huxm 20260606
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:    // added by huxm 20260606
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:    // end of added by huxm 20260606
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:    #endif  // #if LINUX_VERSION_CODE  added by huxm 20260606
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:    hiJPEG_module_exit();       // added by huxm 20260606
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:    HI_S32 v_irq;       // added by huxm 20260606
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:    // added by huxm 20260606
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:    // end of added by huxm 20260606
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:    #endif  // #ifdef LINUX_VERSION_CODE  added by huxm 20260606
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:    // added by huxm 20260606
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:    // end of added by huxm 20260606
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:    #endif  // #if LINUX_VERSION_CODE  added by huxm 20260606
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:// #define FIX_JPGD_REG_RW_CRASHED_BY_HUXM_20260728
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:#ifndef FIX_JPGD_REG_RW_CRASHED_BY_HUXM_20260728
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:    #ifndef FIX_JPGD_REG_RW_CRASHED_BY_HUXM_20260728
    	./msp/drv/jpeg/src/jpeg_drv_osr.c:        hiJPEG_module_init();       // added by huxm 20260606
    	./msp/drv/jpeg/src_dec/jpeg_drv_table.c:        /*  deleted by huxm 20260118
    	./msp/drv/jpeg/src_dec/jpeg_drv_table.c:            replaced by huxm 20260118               */
    	./msp/drv/jpeg/grc_cmm_inc/hi_gfx_comm_k.h:
    						#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size) //added by huxm 20260531
    	./msp/drv/jpeg/grc_cmm_inc/hi_gfx_comm_k.h:/* deleted by huxm 20260118
    	./msp/drv/jpeg/grc_cmm_inc/hi_gfx_comm_k.h:   replaced by huxm 20260118                             */
    	./msp/drv/jpeg/grc_cmm_inc/hi_gfx_comm_k.h:    /*  deleted by huxm 20260118
    	./msp/drv/jpeg/grc_cmm_inc/hi_gfx_comm_k.h:        replaced by huxm 20260118                           */
    	./msp/drv/jpeg/grc_cmm_inc/hi_gfx_comm_k.h:    // HI_UNUSED(pIrqName);    // deleted by huxm 20260118
    	./msp/drv/i2c/std_i2c/drv_i2c.c:#include <linux/of.h>       // added by huxm 20260610
    	./msp/drv/i2c/std_i2c/drv_i2c.c:#include <linux/version.h>  // added by huxm 20260610
    	./msp/drv/i2c/std_i2c/drv_i2c.c:// added by huxm 20260610
    	./msp/drv/i2c/std_i2c/drv_i2c.c:// end of added by huxm 20260610
    	./msp/drv/i2c/std_i2c/drv_i2c.c:    // added by huxm 20260610
    	./msp/drv/i2c/std_i2c/drv_i2c.c:    // end of added by huxm 20260610
    	./msp/drv/i2c/gpio_i2c/drv_gpio_i2c.c:
    					#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size)      //added by huxm 20260531
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_intf.c:#include <linux/timekeeping.h>      // added by huxm 20260531
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_intf.c:#define get_seconds ktime_get_seconds      // added by huxm 20260531
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_intf.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_intf.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_intf.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_intf.c:    #ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_intf.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_intf.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_intf.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_intf.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_intf.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/vdec/vdec_v1.0/drv_vdec_intf.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./msp/drv/aiao/aiao_v1_1/drv_aiao_module.c:#include <linux/version.h>      // added by huxm 20260606
    	./msp/drv/aiao/aiao_v1_1/drv_aiao_module.c:
    								#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20260606
    	./msp/drv/aiao/aiao_v1_1/drv_aiao_module.c:#endif                                 // end of added by huxm 20260606
    	./msp/drv/aiao/aiao_v1_1/drv_aiao_module.c:
    								#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20260606
    	./msp/drv/aiao/aiao_v1_1/drv_aiao_module.c:#endif                              // end of added by huxm 20260606
    	./msp/drv/aiao/aiao_v1_1/ai/drv_ai.c:#include <linux/timekeeping.h>      // added by huxm 20260531
    	./msp/drv/aiao/aiao_v1_1/ai/drv_ai.c:#define get_seconds ktime_get_seconds      // added by huxm 20260531
    	./msp/drv/aiao/aiao_v1_1/ao/drv_ao_op.c:    /* deleted by huxm 20260118
    	./msp/drv/aiao/aiao_v1_1/ao/drv_ao_op.c:    if (pCard != HI_NULL )              // replaced by huxm 20260118
    	./msp/drv/aiao/aiao_v1_1/ao/drv_ao_op.c:    /*  deleted by huxm 20260118
    	./msp/drv/aiao/aiao_v1_1/ao/drv_ao_op.c:    if (pstSndSettings != HI_NULL )       // replaced by huxm 20260118
    	./msp/drv/aiao/aiao_v1_1/ao/drv_ao.c:#include <linux/timekeeping.h>      // added by huxm 20260531
    	./msp/drv/aiao/aiao_v1_1/ao/drv_ao.c:#define get_seconds ktime_get_seconds      // added by huxm 20260531
    	./msp/drv/aiao/aiao_v1_1/ao/hal_aoe_func.c:
    						#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size) //added by huxm 20260531
    	./msp/drv/aiao/aiao_v1_1/ao/drv_ao_track.c:#include <linux/timekeeping.h>      // added by huxm 20260531
    	./msp/drv/aiao/aiao_v1_1/ao/drv_ao_track.c:#define get_seconds ktime_get_seconds      // added by huxm 20260531
    	./msp/drv/aiao/aiao_v1_1/common/src/hal_aiao_priv.c:
    					#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size)   //added by huxm 20260531
    	./msp/drv/aiao/aiao_v1_1/common/src/hal_aiao.c:// added by huxm 20260606
    	./msp/drv/aiao/aiao_v1_1/common/src/hal_aiao.c:// end of added by huxm 20260606
    	./msp/drv/aiao/aiao_v1_1/common/src/hal_aiao.c:// added by huxm 20260606
    	./msp/drv/aiao/aiao_v1_1/common/src/hal_aiao.c:// end of added by huxm 20260606
    	./msp/drv/aiao/aiao_v1_1/common/src/hal_aiao.c:
    								#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20260606
    	./msp/drv/aiao/aiao_v1_1/common/src/hal_aiao.c:#else   // end of added by huxm 20260606
    	./msp/drv/aiao/aiao_v1_1/common/src/hal_aiao.c:#endif      // added by huxm 20260606
    	./msp/drv/vfmw/softlib/Makefile:# added by huxm 20260622
    	./msp/drv/vfmw/softlib/Makefile:# end of added by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_util.c:#include <linux/ktime.h>    // added by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_util.c:    // struct timeval t;       // deleted by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_util.c:    struct timespec64 t;      // replaced by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_util.c:    // do_gettimeofday(&t);   // deleted by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_util.c:    ktime_get_real_ts64(&t);  // replaced by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_util.c:    
    										// gettimeofday(&t, NULL /* &tz */);    // deleted by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_util.c:    ktime_get_real_ts64(&t);    // replaced by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_util.c:    
    						// ret = (UINT64)t.tv_sec * 1000000 + t.tv_usec;        // deleted by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_util.c:    
    						ret = (u64)t.tv_sec * 1000000ULL + t.tv_nsec / 1000;    // replaced by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_util.c:    // struct timeval t;        // deleted by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_util.c:    struct timespec64 t;        // replaced by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_util.c:    // do_gettimeofday(&t);   // deleted by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_util.c:    ktime_get_real_ts64(&t);  // replaced by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_util.c:    
    										// gettimeofday(&t, NULL /* &tz */);    // deleted by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_util.c:    ktime_get_real_ts64(&t);   // replaced by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_util.c:    
    							// ret = (UINT64)t.tv_sec * 1000 + t.tv_usec / 1000;    // deleted by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_util.c:    
    							ret = (u64)t.tv_sec * 1000ULL + t.tv_nsec / 1000000;    // replaced by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/inc/config_imedia.h:
    										// #define __STDC_VERSION__ 199901L       // deleted by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/inc/kernel/math.h:
    														#include <linux/kstrtox.h>  //added by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/inc/kernel/math.h:
    						// #define strtol(x,y,z) simple_strtol(x,y,z)                 // deleted by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/inc/kernel/math.h:
    						extern long strtol(const char *nptr, char **endptr, int base); // replaced by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/inc/kernel/math.h:
    									// #define strtod(x,y) simple_strtol(x,y,0)     // deleted by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/inc/kernel/math.h:
    									#define strtod(x,y) strtol(x,y,0)               // replaced by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/hwcodec/error_resilience.c:    #ifdef  DELETED_BY_HUXM_20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/hwcodec/dsputil.h:#ifdef DELETED_BY_HUXM_20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/hwcodec/utils.c:
    											#include "../inc/kernel/math.h"     // added by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/hwcodec/utils.c:// added by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/hwcodec/utils.c:// end of added by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/hwcodec/eval.c:
    											#include "../inc/kernel/math.h"     // added by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/hwcodec/mpegvideo.c:#ifndef ADDED_BY_HUXM_20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/hwcodec/mpegvideo.c: 
    							// if ((s->avctx->debug_mv) && pict->motion_val)    // deleted by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/hwcodec/mpegvideo.c:      
    						          if (s && pict)                                  // replaced by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/hwcodec/mpegvideo.c:           
    					 // if ((s->avctx->debug & FF_DEBUG_VIS_QP) && pict->motion_val) // deleted by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/hwcodec/mpegvideo.c:            
    						    if (s && pict)                                        // replaced by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/hwcodec/mpegvideo.c:                
    				// if ((s->avctx->debug & FF_DEBUG_VIS_MB_TYPE) && pict->motion_val) // deleted by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/hwcodec/mpegvideo.c:               
    						 if ((s->avctx->debug & FF_DEBUG_VIS_MB_TYPE) && pict)      // deleted by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/hwcodec/mpegvideo.c:#ifdef DELETED_BY_HUXM_20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/hwcodec/h263.c:            #ifndef DELETED_BY_HUXM_20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/hwcodec/h263.c:            #ifdef DELETED_BY_HUXM_20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/hwcodec/parser.c:    
    													// if (avctx->extradata)    // deleted by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/hwdec/hwcodec/parser.c:    
    													if (avctx)                  // replaced by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_ini.c:
    												#include "hwdec/inc/kernel/math.h"  // added by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_viddec.c: #ifdef __BUILD_TIME__        // added by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_viddec.c:  strncpy(pstVersion->cReleaseTime, (const char
    										 *)__BUILD_TIME__, IMEDIA_TIME_LENGTH);    // added by huxm 20260622
    	./msp/drv/vfmw/softlib/hwmedia_v1.1/src/imedia_viddec.c:  #else                   // added by huxm 20260622
    	./msp/drv/vfmw/vfmw_v4.0/firmware/osal/linux_kernel/vfmw_osal.c:
    						#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size)  //added by huxm 20260531
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:// added by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:// end of added by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:
    						#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size) //added by huxm 20260531
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:    struct resource *mem;   // added by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:    // added by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:    // end of added by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:    #endif  // added by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:// added by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:// end of added by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:        .of_match_table = ir_of_match,  // added by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:// added by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:// end of added by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:#endif  // deleted by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:    // added by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:    // end of added by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:    #endif  // deleted by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:    // added by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:    // end of added by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:    #endif  // deleted by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:    // added by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:    // end of added by huxm 20260606
    	./msp/drv/ir/ir_s2/drv_ir_intf.c:    #endif  // deleted by huxm 20260606
    	./msp/drv/png/src/png_hal.c:// added by huxm 20260606
    	./msp/drv/png/src/png_hal.c:// end of added by huxm 20260606
    	./msp/drv/png/src/png_hal.c:// added by huxm 20260606
    	./msp/drv/png/src/png_hal.c:// end of added by huxm 20260606
    	./msp/drv/png/src/png_hal.c:    // added by huxm 20260606
    	./msp/drv/png/src/png_hal.c:    #endif  // #ifdef LINUX_VERSION_CODE  added by huxm 20260606
    	./msp/drv/png/src/png_hal.c:    // end of added by huxm 20260606
    	./msp/drv/png/src/png_osr.c:    hiPNG_module_init();    // added by huxm 20260606
    	./msp/drv/png/src/png_osr.c:    hiPNG_module_init();    // added by huxm 20260606
    	./msp/api/jpeg/src/src_hard_enc/jpge_henc_api.c:      
    				** vi out/..../root/ueventd.bigfish.rc and make kernel            // deleted by huxm 20260606
    	./msp/api/jpeg/src/src_hard_enc/jpge_henc_api.c:      
    				** vi out/..../root/ueventd.Hi3798MX-Platform.rc and make kernel  // replaced by huxm 20260606
    	./msp/api/vdec/vdec_v1.0/mpi_vdec_mjpeg.c:/*  deleted by huxm 20260117
    	./msp/api/vdec/vdec_v1.0/mpi_vdec_mjpeg.c:
    						extern HI_U32 g_lowDelayFrameIndex[HI_VDEC_MAX_INSTANCE_NEW];  //replaced by huxm 20260117
    	./rootfs/busybox/Makefile:# deleted by huxm 20260117    \
    	./rootfs/busybox/Makefile:  replaced by huxm 20260117
    	./rootfs/busybox/Makefile:#added by huxm 20260118
    	./rootfs/iperf/Makefile:#deleted by huxm 20260129
    	./rootfs/iperf/Makefile:#replaced by huxm 20260129
    	./rootfs/iperf/Makefile:# delted by huxm 20260129
    	./rootfs/iperf/Makefile:# replaced by huxm 20260129
    	./rootfs/iperf/Makefile:# delted by huxm 20260129
    	./rootfs/iperf/Makefile:# replaced by huxm 20260129
    	./rootfs/dropbear/Makefile:# deleted by huxm 20260129
    	./rootfs/dropbear/Makefile:# replaced by huxm 20260129
    	./rootfs/filecap/Makefile:#deleted by huxm 20260129
    	./rootfs/filecap/Makefile:#replaced by huxm 20260129
    	./rootfs/filecap/Makefile:#endif replaced by huxm 20260129
    	./rootfs/filecap/Makefile:# deleted by huxm 20260129
    	./rootfs/filecap/Makefile:# replaced by huxm 20260129
    	./rootfs/sysstat/Makefile:# deleted by huxm 20260129
    	./rootfs/sysstat/Makefile:# replaced  by huxm 20260129
    	./rootfs/sysstat/Makefile:# delted by huxm 20260129
    	./rootfs/sysstat/Makefile:# replaced by huxm 20260129
    	./rootfs/Makefile:# deleted by huxm 20260126
    	./rootfs/Makefile:# replaced by huxm 20260126
    	./rootfs/mtd-utils/Makefile:#deleted by huxm 20260129
    	./rootfs/mtd-utils/Makefile:#replaced by huxm 20260129
    	./rootfs/iptables/Makefile:#deleted by huxm 20260129
    	./rootfs/iptables/Makefile:# replaced by huxm 20260129
    	./rootfs/iptables/Makefile:#deleted by huxm 20260129
    	./rootfs/iptables/Makefile:# replaced by huxm 20260129
    	./rootfs/iptables/Makefile:# delted by huxm 20260129
    	./rootfs/iptables/Makefile:# replaced by huxm 20260129
    	./rootfs/pppd/Makefile:#deleted by huxm 20260129
    	./rootfs/pppd/Makefile:#replaced by huxm 20260129
    	./rootfs/pppd/Makefile:# deleted by huxm 20260129
    	./rootfs/pppd/Makefile:# deleted by huxm 20260129
    	./rootfs/pppd/Makefile:#replaced by huxm 20260129
    	./rootfs/gdb/Makefile:# deleted by huxm 20260129
    	./rootfs/gdb/Makefile:# replaced by huxm 20260129
    	./rootfs/gdb/Makefile:#added by huxm 20260129
    	./rootfs/gdb/Makefile:# deleted by huxm 20260129
    	./rootfs/gdb/Makefile:# replaced by huxm 20260129
    	./rootfs/mii-tool/Makefile:# deleted by huxm 20260130
    	./rootfs/mii-tool/Makefile:# replaced by huxm 20260130
    	./rootfs/mii-tool/Makefile:# deleted by huxm 20260130
    	./rootfs/mii-tool/Makefile:# replaced by huxm 20260130
    	./boot/product/android/recovery.c:  // printf("bigfish __recovery__ok");               // deleted by huxm 20260606
    	./boot/product/android/recovery.c:  printf("Hi3798MX-Platform __recovery__ok");       // replaced by huxm 20260606
    	./component/openssl/Makefile:# deleted by huxm 20260612
    	./component/openssl/Makefile:# replaced by huxm 20260612
    	./component/exfat/Makefile:#            deleted by huxm 20260118
    	./component/alsa/Makefile:# deleted by huxm 20260126
    	./component/alsa/Makefile:# replaced by huxm 20260126
    	./component/alsa/Makefile:# deleted by huxm 20260612
    	./component/alsa/Makefile:# replaced by huxm 20260612
    	./component/alsa/Makefile:# deleted by huxm 20260612
    	./component/alsa/Makefile:# replaced by huxm 20260612
    	./component/alsa/Makefile:# deleted by huxm 20260612
    	./component/alsa/Makefile:# replaced by huxm 20260612
    	./component/alsa/Makefile:# deleted by huxm 20260612
    	./component/alsa/Makefile:# replaced by huxm 20260612
    	./component/alsa/Makefile:# deleted by huxm 20260126
    	./component/alsa/Makefile:# replaced by huxm 20260126
    	./common/drv/stat/drv_stat_ext.c:#include <linux/version.h> // added by huxm 20260602
    	./common/drv/stat/drv_stat_ext.c:// added by huxm 20260603
    	./common/drv/stat/drv_stat_ext.c:// end of added by huxm 20260603
    	./common/drv/stat/drv_stat_ext.c:    // added by huxm 20260603
    	./common/drv/stat/drv_stat_ext.c:    // end of added by huxm 20260603
    	./common/drv/stat/drv_stat_ext.c:    // added by huxm 20260603
    	./common/drv/stat/drv_stat_ext.c:    // end of added by huxm 20260603
    	./common/drv/stat/drv_stat_ext.c:    #endif  // added by huxm 20260603
    	./common/drv/mmz/drv_media_mem.c:
    				#include "../../kernel/linux-5.15.134/drivers/staging/android/ion/ion.h"  // added by huxm 20260603
    	./common/drv/mmz/drv_mmz_userdev.c:
    			#include "../../kernel/linux-5.15.134/drivers/staging/android/ion/ion.h"     // added by huxm 20260603
    	./common/drv/proc/drv_proc_ext_k.c:#include <linux/version.h> // added by huxm 20260602
    	./common/drv/proc/drv_proc_ext_k.c:  #if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0) // added by huxm 20260602
    	./common/drv/proc/drv_proc_ext_k.c:    struct fd fd_file;                               // added by huxm 20260602
    	./common/drv/proc/drv_proc_ext_k.c:    #endif                                           // added by huxm 20260602
    	./common/drv/proc/drv_proc_ext_k.c:    // added by huxm 20260602
    	./common/drv/proc/drv_proc_ext_k.c:    // end of added by huxm 20260602
    	./common/drv/proc/drv_proc_ext_k.c:    #endif  // added by huxm 20260602
    	./common/drv/proc/drv_proc_ext_k.c:        
    								#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20260603
    	./common/drv/proc/drv_proc_ext_k.c:             
    								ret = kernel_write(file, buf, strlen(buf), &pos);       // added by huxm 20260603
    	./common/drv/proc/drv_proc_ext_k.c:        #else                                        // added by huxm 20260603
    	./common/drv/proc/drv_proc_ext_k.c:        #endif                                       // added by huxm 20260603
    	./common/drv/sys/drv_sys_ext.c:
    					#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size)    // added by huxm 20260602
    	./common/drv/sys/drv_sys_ext_k.c:
    					#define ioremap_nocache(physaddr, size)   ioremap(physaddr, size)    // added by huxm 20260602
    	./common/drv/log/drv_log_ext_k.c:#ifdef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./common/drv/log/drv_log_ext_k.c:#ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./common/drv/log/drv_log_ext_k.c:        #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./common/drv/log/drv_log_ext_k.c:    #ifndef ADDED_BY_HUXM_20260701_FOR_KASAN_FRAME_LARGER_THAN_1024
    	./common/include/hi_debug.h:/*      deleted by huxm 20260117
    	./common/include/hi_debug.h:#define VERSION_STRING 
    									("SDK_VERSION:[" MKMARCOTOSTR(SDK_VERSION) "]") // added by huxm 20260117
    	./common/include/hi_type.h:#define    UNUSED(x) ((x)=(x))    // added by huxm 20260118
    	./kernel/linux-5.15.134/Makefile:# -Werror-implicit-function-declaration  
    							--->  -Wno-implicit-function-declaration  modify by huxm 20260529 for source/msp/drv/*
    	./kernel/linux-5.15.134/arch/arm/boot/compressed/head.S:; #define DEBUG 1     ; deleted by huxm 20260829
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:              // added by huxm 20260606
    	./kernel/linux-5.15.134/arch/arm/boot/dts/hi3798mv100.dts:              // end of added by huxm 20260606
    	./kernel/linux-5.15.134/arch/arm/mach-hi3798mx/core.c:
    						// DT_MACHINE_START(HI3798MX, "bigfish")                  // deleted by huxm 20260606
    	./kernel/linux-5.15.134/arch/arm/mach-hi3798mx/core.c:
    							DT_MACHINE_START(HI3798MX, "Hi3798MX-Platform")           // replaced by huxm 20260606
    	./kernel/linux-5.15.134/include/linux/hisilicon/freq.h:
    											#define _27MHz           (27000000)     // added by huxm 20260101
    	./kernel/linux-5.15.134/include/linux/hisilicon/freq.h:
    											#define _54MHz           (54000000)     // added by huxm 20260101
    	./kernel/linux-5.15.134/include/linux/hisilicon/freq.h:
    											#define _83dot3MHz       (83300000)     // added by huxm 20260101
    	./kernel/linux-5.15.134/include/dt-bindings/clock/hi3798mv100-clock.h:// added by huxm 20260101
    	./kernel/linux-5.15.134/include/dt-bindings/clock/hi3798mv100-clock.h:// added by huxm 20260101
    	./kernel/linux-5.15.134/drivers/staging/android/ion/hisi/hisi_ion.c:
    												// module_exit(hisi_ion_exit);      // deleted by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion_system_heap.c:
    												#include <linux/version.h>         // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion_system_heap.c:// added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion_system_heap.c:// end of added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion_system_heap.c:#endif    // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion_system_heap.c:  // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion_system_heap.c:  // end of added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion_system_heap.c:  #endif  // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion_heap.c:
    									#include <linux/version.h>                     // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion_heap.c:
    									#include <uapi/linux/sched/types.h>              // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion_heap.c: // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion_heap.c: // end of added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion_heap.c: #endif  // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c
    										:#include <linux/version.h>                    // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:
    										#include <linux/huge_mm.h>                    // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:             
    				// zap_page_range(vma, vma->vm_start, vma->vm_end - vma->vm_start,NULL);// deleted by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:              
    					zap_page_range(vma, vma->vm_start, vma->vm_end - vma->vm_start);    // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:// added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:// end of added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:      // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:      // end of added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:      #endif  // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:// added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:// end of added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:#endif // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:// added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:// end of added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:#endif        // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:      
    								#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c: return 0;                    // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:      #endif                 // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:      // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:      // end of added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:      // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:      // end of added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:      #endif  // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:                      // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:                      // end of added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:                      #endif  // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:                      // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:                      // end of added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/staging/android/ion/ion.c:                      #endif // added by huxm 20260603
    	./kernel/linux-5.15.134/drivers/mmc/host/himciv200/himciv200.c:
    												#include <linux/version.h>       // added by huxm 20260720
    	./kernel/linux-5.15.134/drivers/mmc/host/himciv200/himciv200.c:
    								#if LINUX_VERSION_CODE >= KERNEL_VERSION(5, 15, 0)      // added by huxm 20260720
    	./kernel/linux-5.15.134/drivers/mmc/host/himciv200/himciv200.c:   	#else      // end of added by huxm 20260720
    	./kernel/linux-5.15.134/drivers/mmc/host/himciv200/himciv200.c:#endif        // added by huxm 20260720
    	./kernel/linux-5.15.134/drivers/mmc/host/himciv200/himciv200.c:
    						 /*      --------------------  added by huxm 20260720    -----------------------------*/
    	./kernel/linux-5.15.134/drivers/mmc/host/himciv200/himciv200.c: 
    						/*      -----------------  end of added by huxm 20260720 -----------------------------*/
    	./kernel/linux-5.15.134/drivers/mmc/host/himciv200/himciv200.c:
    				// static int __init himciv200_pltm_probe(struct platform_device *pdev)// deleted by huxm 20260101
    	./kernel/linux-5.15.134/drivers/mmc/host/himciv200/himciv200.c:
    						static int himciv200_pltm_probe(struct platform_device *pdev) // added by huxm 20260101
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:
    												#include <linux/slab.h>   // added by huxm 20260820
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:
    												#include <linux/cpuhotplug.h>// added by huxm 20260820
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:
    												#include <linux/clocksource.h>// added by huxm 20260820
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:
    											#define           ADOPTED_KERNEL_VERSION_5_15_BY_HUXM_20260820
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:
    											#define               USE_CLOCKSOURCE_MMIO_BY_HUXM_20260822
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:#ifndef      USE_CLOCKSOURCE_MMIO_BY_HUXM_20260822
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:#ifdef      USE_CLOCKSOURCE_MMIO_BY_HUXM_20260822
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:
    											#ifndef   ADOPTED_KERNEL_VERSION_5_15_BY_HUXM_20260820
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:
    											#ifdef    ADOPTED_KERNEL_VERSION_5_15_BY_HUXM_20260820
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:
    											#ifndef           USE_CLOCKSOURCE_MMIO_BY_HUXM_20260822
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:
    								#else /* ----------- USE_CLOCKSOURCE_MMIO_BY_HUXM_20260822     ---------*/
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:
    							#endif    /* ----------- USE_CLOCKSOURCE_MMIO_BY_HUXM_20260822     ---------*/
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:
    												#ifdef     ADOPTED_KERNEL_VERSION_5_15_BY_HUXM_20260820
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:
    											#ifdef            ADOPTED_KERNEL_VERSION_5_15_BY_HUXM_20260820
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:
    											#ifdef            ADOPTED_KERNEL_VERSION_5_15_BY_HUXM_20260820
    	./kernel/linux-5.15.134/drivers/hisilicon/clocksource/timer.c:  
    													#ifdef ADOPTED_KERNEL_VERSION_5_15_BY_HUXM_20260820
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/hi3798mx/clk-hi3798mv100.c:
    								/* deleted .offset = _id replaced .offset=_offset by huxm 20260103     */
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.c:       
    									// __hisi_clk_reset(clk);       // deleted by huxm 20260101
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.c: pr_debug("%s: %s offset:%#x peri_crgx:%p \n",
    							 __func__, clk->name, clk->offset, clk->peri_crgx);   // added by huxm 20260101
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.c:      
    									 // clk->flags |= CLKHW_RESET;           // delted by huxm 20260101
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.c:       
    									__hisi_clk_disable(clk);                        // added by huxm 20260101
    	./kernel/linux-5.15.134/drivers/hisilicon/clk/clk-hisi.c:       
    												__hisi_clk_unreset(clk);        // added by huxm 20260101
    	./kernel/linux-5.15.134/drivers/Kconfig:# added by huxm 20260625
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/phy.c://extern void __iomem * 
    						ioremap_nocache(unsigned long offset, unsigned long size);     // added by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/phy.c:#define ioremap_nocache(physaddr, size)   
    									     ioremap(physaddr, size)                // added by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.h:     
    										struct net_device *netdev;              // added by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.h:        // by huxm 20260115  
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/mdio.c:      // deleted by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:
    											#include <linux/refcount.h>          // added by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:
    											#include <linux/if_ether.h>          // added by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:
    					/* ------------------------------  added by huxm 20260830 ------------------------------*/
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:
    									#define              FIX_DMA_MAP_BY_HUXM_20260830
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:
    					/* ---------------------------- endif added by huxm 20260830 ----------------------------*/
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:		// added by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:             
    					/* ------------------------------  added by huxm 20260830 ------------------------------*/
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:                             
    												#ifdef          FIX_DMA_MAP_BY_HUXM_20260830
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:             
    					/* ---------------------------- endif added by huxm 20260830 ----------------------------*/
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:            
    								 #ifndef FIX_DMA_MAP_BY_HUXM_20260830
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     
    					/* ------------------------------  added by huxm 20260830 ------------------------------*/
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     
    					/* ---------------------------- endif added by huxm 20260830 ----------------------------*/
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     
    										//atomic_inc(&skb->users);              // deleted by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     
    										refcount_inc(&skb->users);           // replaced by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:      #ifndef FIX_DMA_MAP_BY_HUXM_20260830
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     
    						/* ------------------------------  added by huxm 20260830 ------------------------------*/
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     
    						/* ---------------------------- endif added by huxm 20260830 ----------------------------*/
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:                    
    												 #ifndef         FIX_DMA_MAP_BY_HUXM_20260830
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:             
    						/* ------------------------------  added by huxm 20260830 ------------------------------*/
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:            
    					 /* ---------------------------- endif added by huxm 20260830 ----------------------------*/
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:
    						static void hieth_monitor_func(struct timer_list *t)         // replaced by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:          //  deleted by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:
    						//static void hieth_net_timeout(struct net_device *dev)       // deleted by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:
    			static void hieth_net_timeout(struct net_device *dev, unsigned int txqueue) // replaced by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:                     
    									#ifndef FIX_DMA_MAP_BY_HUXM_20260830
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     
    						/* ----------------------------  added by huxm 20260830 ----------------------------*/
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     
    						/* ---------------------------- endif added by huxm 20260830 ----------------------------*/
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     
    		// hieth_xmit_real_send(priv, skb); // moved to after tx_bytes update (which uses skb->len) (by huxm 20260830)
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     
    									//dev->trans_start = jiffies;   // removed from active code (by huxm 20260114)
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     netif_trans_update(dev);                        // replaces the old dev->trans_start = jiffies (by huxm 20260114)
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     hieth_local_lock(priv);                         // Acquire lock to protect tx statistics updates from concurrent access(by huxm 20260830)
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     hieth_local_unlock(priv);                       // Release lock after tx statistics updates are completed(by huxm 20260830)
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     hieth_xmit_real_send(priv, skb);     
    									   // relocated to after tx_bytes update (which uses skb->len) (by huxm 20260830)
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:/*           // deleted by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:// replaced by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:// replaced by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     //.get_settings = 
    											hieth_ethtools_get_settings,          // deleted by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     //.set_settings = 
    											hieth_ethtools_set_settings,          // deleted by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     .get_link_ksettings = 
    												hieth_ethtools_get_settings,      // replaced by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     .set_link_ksettings = 
    												hieth_ethtools_set_settings,      // replaced by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:            
    													 // dev->last_rx = jiffies;      // deleted by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     
    											// if (hieth_phy_param[port].macaddr){    //deleted by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:  
    							 is_valid_ether_addr(hieth_phy_param[port].macaddr)){  // replaced by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c: pr_debug("[%s]:macaddr = 
    									%pM\n",__func__,hieth_phy_param[port].macaddr);   // added by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:}else{   // added by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     
    													priv->netdev = netdev;          // added by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     //  deleted by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:    
    						 timer_setup(&priv->monitor, hieth_monitor_func, 0);             // replaced by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:
    					//   pr_info("attached port %d PHY %d to driver %s\n",               // deleted by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:           
    							  port, priv->phy->mdio.addr, priv->phy->drv->name);      // replaced by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     /* added by huxm 20260114       */
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:     
    							        /* get phy_mode                                 deleted by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:  
    			           ret = of_get_phy_mode(child, &phy_mode);                         // replaced by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:      
    		               //hieth_phy_param[idx].phy_mode = phy_mode;                        // deleted by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c: memcpy((void *)
    				(&hieth_phy_param[idx].phy_mode), &phy_mode, sizeof(phy_interface_t));  // replaced by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c: // get mac // deleted by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:             
    						ret = of_get_mac_address(child, macaddr);                  // replaced by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:    
    	                 //hieth_phy_param[idx].macaddr = macaddr;                          // deleted by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:   
    	                  ether_addr_copy(hieth_phy_param[idx].macaddr,macaddr);          // replaced by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/hi3798mveth/hieth.c:    
    			         eth_random_addr(hieth_phy_param[idx].macaddr);                    // added by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/Makefile:#added by huxm 20260114
    	./kernel/linux-5.15.134/drivers/net/ethernet/hisilicon/Kconfig:# added by huxm 20260114
    

## Support

若本文对你的学习与工作有所帮助、启发，欢迎支持！  
[SupportQR](../Support/SupportQR.md)
