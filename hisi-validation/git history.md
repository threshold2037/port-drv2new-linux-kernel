commit df990c8c32d40038aca4fe9a64d1b7d5452e955f
Author: Linux Kernel Upgrade <Upgrade@email.system>
Date:   Sat Sep 26 15:02:16 2026 +0800

     fix(fastboot): resolve undefined instruction and data abort errors
        - Add -fno-delete-null-pointer-checks to prevent GCC12's erroneous path isolation optimization from turning null pointer UB into undefined instruction traps.
        - Add -mno-unaligned-access to fix unaligned ldrh accesses in download_process(), which caused undefined instruction and data abort before the head-frame CRC check.
        - Add -mfloat-abi=soft to prevent GCC12 from auto-vectorizing ordinary C code and thus generating NEON/VFP instructions.
        - Add __attribute__((packed)) to IP_t in NetSetIP to prevent GCC12 store-merging from generating a 32-bit store to a 2-byte aligned  address, which triggered an ARM unaligned access data abort.
    

commit a7545a39d3e4102ed58393c92ec0ad28c879c7e0
Author: Linux Kernel Upgrade <Upgrade@email.system>
Date:   Sat Sep 12 17:24:56 2026 +0800

    fix: Fix hi_cpufreq crash on 5.15 and replace interactive governor with conservative
    
    The cpufreq driver crashed when switching to ondemand/powersave/conservative governors
    because freqs.policy was used uninitialized in hi_cpufreq_scale(). Remove
    the obsolete for_each_online_cpu loops and use policy->cached_resolved_idx
    to get the correct frequency table index in hi_cpufreq_target(), fixing the
    kernel Oops under Linux 5.15.
    
    Also update the module load script to use conservative governor instead of
    interactive, which was removed in Linux 5.15. Adjust sampling_rate and
    freq_step parameters accordingly.
    

commit be9699c0918e948e87dd88df4c75b3f9506f8237
Author: Linux Kernel Upgrade <Upgrade@email.system>
Date:   Wed Sep 9 18:10:59 2026 +0800

    drivers: msp: adsp: strip empty .arm_vfe_header section
    
    Remove the unused non-allocatable .arm_vfe_header section from objects
    extracted from libimedia_asrc_arma9.a to silence the modpost warning.
    Also fix shell command substitution so 'ar t' runs after cd into the
    library directory.
    

commit 7258669007a8fdc896c88f2724f06c5714a179fd
Author: Linux Kernel Upgrade <Upgrade@email.system>
Date:   Wed Sep 9 17:07:34 2026 +0800

    Remove __init annotation from hi_init_opp_table declaration in pm/hi_opp_data.h to fix modpost section mismatch warning
    

commit 17ead28a28d837566250921d2dfd0c1b9c17f71b
Author: Linux Kernel Upgrade <Upgrade@email.system>
Date:   Wed Sep 9 16:50:43 2026 +0800

    Remove __init annotation from gpu_init_clocks declaration in mali450/mali4xx_clk.h to fix modpost section mismatch warning
    

commit db5600cac79eb1779c1f805a766096f4e559b3b0
Author: Linux Kernel Upgrade <Upgrade@email.system>
Date:   Wed Sep 9 13:25:14 2026 +0800

    mali: fix API_VERSION extraction path in Kbuild
    

commit fef2b55dabc7aef43de28d745e57a5df1203220e
Author: Linux Kernel Upgrade <Upgrade@email.system>
Date:   Wed Sep 9 11:23:05 2026 +0800

    fix: adsp: add -fno-short-wchar to fix wchar_t size mismatch warning
    
    Add ccflags-y += -fno-short-wchar to drivers/msp/adsp/Makefile so all ADSP objects consistently use 4-byte wchar_t. This resolves the arm-hisi-linux-gnueabi-ld warnings about objects compiled with 2-byte wchar_t while the output expects 4-byte wchar_t.
    

commit 1b4e5a910f759a57234aec0c513bf54a91d4ca63
Author: Linux Kernel Upgrade <Upgrade@email.system>
Date:   Tue Sep 8 20:46:16 2026 +0800

    Fix Kconfig timer choice symbol conflict by renaming duplicated HI3798MV2X symbols to HI3796MV2X in mach-hi3796mv2x
    

commit 6af2f16ed70d928bc363774d461f74c9af54ba40 (HEAD -> master)
Author: Linux Kernel Upgrade <Upgrade@email.system>
Date:   Wed Sep 2 16:19:08 2026 +0800

    Clean up redundant debug information in *.ko modules and DEBUG settings in .config
    

commit 7c59ee9b9f87d2e928ea961d5216e3fd4fd89270
Author: Linux Kernel Upgrade <Upgrade@email.system>
Date:   Tue Sep 1 17:15:18 2026 +0800

    1. Fix eth0 NIC driver, KASAN use-after-free or slab-out-of-bounds errors
    2. Fix DMA-API: cacheline tracking EEXIST, overlapping mappings aren't supported error
    

commit 225e5e25b355c99dde32545504064bee0708ef59
Author: Linux Kernel Upgrade <Upgrade@email.system>
Date:   Sat Aug 29 23:23:30 2026 +0800

    Review the troubleshooting process for the hung issue after 'Starting kernel ... Uncompressing Linux... done, booting the kernel.' and remove debug information used during debugging.
    

commit 698e1ed92444b3f128410e04d33ba426c1bf9eab
Author: Linux Kernel Upgrade <Upgrade@email.system>
Date:   Wed Aug 26 13:36:42 2026 +0800

    clocksource and clockevent rewrite, improved using Linux-5.15 kernel's built-in driver arm,sp804 which lacks high-resolution timer
    1. The functions setup_irq, remove_irq, register_cpu_notifier may have been removed or no longer exported as symbols in Linux-5.15 kernel; rewritten and tested using request_irq(), free_irq(), and cpuhp_setup_state_nocalls.
    2. Replaced clocksource_register_hz with clocksource_mmio_init for more efficient and reasonable code.
    

commit 09483347039e197e7d9e660c42e12e6fe769ae5d
Author: Linux Kernel Upgrade <Upgrade@email.system>
Date:   Mon Aug 24 15:13:34 2026 +0800

    Clean up debug messages in clock controller (clk.c, clk-hi3798mv100.c) and fix a bug in EMMC host driver (himciv200.c); also remove stale Kconfig/Makefile fragments
    

commit 227f7fa9280e6498fec8e9bef12097fb7f6d5edc
Author: Linux Kernel Upgrade <Upgrade@email.system>
Date:   Mon Aug 10 15:18:59 2026 +0800

    fix: resolve driver bugs in sample/higo/sample_dec and improve clock controller
    
    Fix the driver issues found during testing of sample/higo/sample_dec, which also triggered a rework of the previous fix for loading hi_*.ko modules. Additionally, refine the incomplete parts of the clock controller implementation.
    

commit 1fbf49cc86201b583e18dc8fbf1a6bc5ad4a85c5
Author: Linux Kernel Upgrade <Upgrade@email.system>
Date:   Wed Jul 22 14:24:58 2026 +0800

    Fix drivers for insmod of hi_*.ko modules
    

......省略，只展示最近的部分。
