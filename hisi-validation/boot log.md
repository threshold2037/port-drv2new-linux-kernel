
    Starting kernel ...
    
    Uncompressing Linux... done, booting the kernel.
    Booting Linux on physical CPU 0x0
    Linux version 5.15.134_s40 (u2204@u2204) (arm-hisi-linux-gnueabi-gcc.br_real (Buildroot -gbfb24b47) 12.3.0, 
    	GNU ld (GNU Binutils) 2.40) #418 SMP Wed Sep 2 15:21:12 CST 2026
    CPU: ARMv7 Processor [410fc075] revision 5 (ARMv7), cr=10c5387d
    CPU: div instructions available: patching division code
    CPU: PIPT / VIPT nonaliasing data cache, VIPT aliasing instruction cache
    OF: fdt: Machine model: Hisilicon
    Memory policy: Data cache writealloc
    DSP run memory space at 0x02000000, size: 0x00800000 Bytes.
    cma: Reserved 400 MiB at 0x27000000
    cma: Reserved 4 MiB at 0x26c00000
    Zone ranges:
      Normal   [mem 0x0000000000000000-0x000000003fffffff]
      HighMem  empty
    Movable zone start for each node
    Early memory node ranges
      node   0: [mem 0x0000000000000000-0x000000003fffffff]
    Initmem setup node 0 [mem 0x0000000000000000-0x000000003fffffff]
    percpu: Embedded 11 pages/cpu s15756 r8192 d21108 u45056
    Built 1 zonelists, mobility grouping on.  Total pages: 260096
    Kernel command line: root=/dev/nfs nfsroot=192.168.30.100:/,nfsvers=4.0,proto=tcp timeo=20 rw ip=192.168.30.10:192.168.30.100:192.168.30.1:255.255.255.0::eth0:off console=ttyAMA0,115200 mmz=ddr,0,0,400M vmalloc=500M bootdelay=3  mem=1G
    printk: log_buf_len individual max cpu contribution: 4096 bytes
    printk: log_buf_len total cpu_extra contributions: 12288 bytes
    printk: log_buf_len min size: 16384 bytes
    printk: log_buf_len: 32768 bytes
    printk: early log buf free: 14708(89%)
    Dentry cache hash table entries: 131072 (order: 7, 524288 bytes, linear)
    Inode-cache hash table entries: 65536 (order: 6, 262144 bytes, linear)
    mem auto-init: stack:off, heap alloc:off, heap free:off
    Memory: 603252K/1048576K available (9216K kernel code, 412K rwdata, 1964K rodata, 1024K init, 574K bss, 31628K reserved, 413696K cma-reserved, 0K highmem)
    SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
    rcu: Hierarchical RCU implementation.
    rcu: RCU calculated value of scheduler-enlistment delay is 100 jiffies.
    NR_IRQS: 352
    clocksource: hisi-timer: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 79635851949 ns
    sched_clock: 32 bits at 24MHz, resolution 41ns, wraps every 89478484971ns
    Console: colour dummy device 80x30
    Calibrating delay loop... 2383.87 BogoMIPS (lpj=1191936)
    CPU: Testing write buffer coherency: ok
    pid_max: default: 32768 minimum: 301
    Mount-cache hash table entries: 2048 (order: 1, 8192 bytes, linear)
    Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes, linear)
    CPU0: update cpu_capacity 1024
    CPU0: thread -1, cpu 0, socket 0, mpidr 80000000
    Setting up static identity map for 0x100000 - 0x100060
    rcu: Hierarchical SRCU implementation.
    CPU: hi3798mv100
    smp: Bringing up secondary CPUs ...
    CPU1: update cpu_capacity 1024
    CPU1: thread -1, cpu 1, socket 0, mpidr 80000001
    CPU2: update cpu_capacity 1024
    CPU2: thread -1, cpu 2, socket 0, mpidr 80000002
    CPU3: update cpu_capacity 1024
    CPU3: thread -1, cpu 3, socket 0, mpidr 80000003
    smp: Brought up 1 node, 4 CPUs
    SMP: Total of 4 processors activated (9572.35 BogoMIPS).
    CPU: All CPU(s) started in SVC mode.
    devtmpfs: initialized
    VFP support v0.3: implementor 41 architecture 2 part 30 variant 7 rev 5
    DMA-API: preallocated 65536 debug entries
    DMA-API: debugging enabled by kernel config
    clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 1911260446275000 ns
    futex hash table entries: 1024 (order: 4, 65536 bytes, linear)
    NET: Registered PF_NETLINK/PF_ROUTE protocol family
    DMA: preallocated 256 KiB pool for atomic coherent allocations
    hw-breakpoint: found 5 (+1 reserved) breakpoint and 4 watchpoint registers.
    hw-breakpoint: maximum watchpoint size is 8 bytes.
    Serial: AMBA PL011 UART driver
    f8b00000.uart: ttyAMA0 at MMIO 0xf8b00000 (irq = 20, base_baud = 0) is a PL011 rev2
    printk: console [ttyAMA0] enabled
    f8006000.uart: ttyAMA1 at MMIO 0xf8006000 (irq = 21, base_baud = 0) is a PL011 rev2
    f8b02000.uart: ttyAMA2 at MMIO 0xf8b02000 (irq = 22, base_baud = 0) is a PL011 rev2
    kprobes: kprobe jump-optimization is enabled. All kprobes are optimized if possible.
    SCSI subsystem initialized
    ssp-pl022 f8b1a000.spi: ARM PL022 driver, device ID: 0x00041022
    ssp-pl022 f8b1a000.spi: mapped registers from 0xf8b1a000 to (ptrval)
    spi_master spi0: will run message pump with realtime priority
    usbcore: registered new interface driver usbfs
    usbcore: registered new interface driver hub
    usbcore: registered new device driver usb
    mc: Linux media interface: v0.10
    videodev: Linux video capture interface: v2.00
    Bluetooth: Core ver 2.22
    NET: Registered PF_BLUETOOTH protocol family
    Bluetooth: HCI device and connection manager initialized
    Bluetooth: HCI socket layer initialized
    Bluetooth: L2CAP socket layer initialized
    Bluetooth: SCO socket layer initialized
    clocksource: Switched to clocksource hisi-timer
    VFS: Disk quotas dquot_6.6.0
    VFS: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
    NET: Registered PF_INET protocol family
    IP idents hash table entries: 16384 (order: 5, 131072 bytes, linear)
    tcp_listen_portaddr_hash hash table entries: 512 (order: 0, 6144 bytes, linear)
    Table-perturb hash table entries: 65536 (order: 6, 262144 bytes, linear)
    TCP established hash table entries: 8192 (order: 3, 32768 bytes, linear)
    TCP bind hash table entries: 8192 (order: 4, 65536 bytes, linear)
    TCP: Hash tables configured (established 8192 bind 8192)
    UDP hash table entries: 512 (order: 2, 16384 bytes, linear)
    UDP-Lite hash table entries: 512 (order: 2, 16384 bytes, linear)
    NET: Registered PF_UNIX/PF_LOCAL protocol family
    RPC: Registered named UNIX socket transport module.
    RPC: Registered udp transport module.
    RPC: Registered tcp transport module.
    RPC: Registered tcp NFSv4.1 backchannel transport module.
    NetWinder Floating Point Emulator V0.97 (double precision)
    Initialise system trusted keyrings
    workingset: timestamp_bits=30 max_order=18 bucket_order=0
    squashfs: version 4.0 (2009/01/31) Phillip Lougher
    NFS: Registering the id_resolver key type
    Key type id_resolver registered
    Key type id_legacy registered
    jffs2: version 2.2 (NAND) (ZLIB) (RTIME) (c) 2001-2006 Red Hat, Inc.
    fuse: init (API version 7.34)
    Key type asymmetric registered
    Asymmetric key parser 'x509' registered
    Block layer SCSI generic (bsg) driver version 0.4 loaded (major 251)
    io scheduler mq-deadline registered
    io scheduler kyber registered
    pl061_gpio gpio0: PL061 GPIO chip registered
    pl061_gpio gpio1: PL061 GPIO chip registered
    pl061_gpio gpio2: PL061 GPIO chip registered
    pl061_gpio gpio3: PL061 GPIO chip registered
    pl061_gpio gpio4: PL061 GPIO chip registered
    pl061_gpio gpio5: PL061 GPIO chip registered
    pl061_gpio gpio6: PL061 GPIO chip registered
    brd: module loaded
    loop: module loaded
    hieth: attached port 0 PHY 2 to driver Generic PHY
    PPP generic driver version 2.4.2
    PPP BSD Compression module registered
    PPP Deflate Compression module registered
    ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
    ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
    usbcore: registered new interface driver cdc_wdm
    usbcore: registered new interface driver usb-storage
    usbcore: registered new interface driver usbserial_generic
    usbserial: USB Serial support registered for generic
    usbcore: registered new interface driver ftdi_sio
    usbserial: USB Serial support registered for FTDI USB Serial Device
    usbcore: registered new interface driver option
    usbserial: USB Serial support registered for GSM modem (1-port)
    usbcore: registered new interface driver pl2303
    usbserial: USB Serial support registered for pl2303
    mousedev: PS/2 mouse device common for all mice
    i2c_dev: i2c /dev entries driver
    usbcore: registered new interface driver uvcvideo
    sp805-wdt f8a2c000.watchdog: registration successful
    usbcore: registered new interface driver btusb
    registered new interface driver himciv200
    mmc0: new DDR MMC card at address 0001
    mmcblk0: mmc0:0001 P1XXXX 3.57 GiB
    mmcblk0boot0: mmc0:0001 P1XXXX 2.00 MiB
    mmcblk0boot1: mmc0:0001 P1XXXX 2.00 MiB
    mmcblk0rpmb: mmc0:0001 P1XXXX 128 KiB, chardev (250:0)
    f9820000.himciv200.SD: eMMC/MMC/SD Device NOT detected!
    usbcore: registered new interface driver usbhid
    usbhid: USB HID core driver
    hiotg: registered new interface otg driver
    NET: Registered PF_INET6 protocol family
    Segment Routing with IPv6
    In-situ OAM (IOAM) with IPv6
    NET: Registered PF_PACKET protocol family
    Bridge firewalling registered
    Bluetooth: RFCOMM TTY layer initialized
    Bluetooth: RFCOMM socket layer initialized
    Bluetooth: RFCOMM ver 1.11
    Bluetooth: BNEP (Ethernet Emulation) ver 1.3
    Bluetooth: BNEP filters: protocol multicast
    Bluetooth: BNEP socket layer initialized
    Bluetooth: HIDP (Human Interface Emulation) ver 1.2
    Bluetooth: HIDP socket layer initialized
    8021q: 802.1Q VLAN Support v1.8
    Key type dns_resolver registered
    Registering SWP/SWPB emulation handler
    Loading compiled-in X.509 certificates
    hieth f9840000.hieth eth0: Link is Up - 100Mbps/Full - flow control off
    IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
    IP-Config: Complete:
         device=eth0, hwaddr=00:18:52:f5:de:14, ipaddr=192.168.30.10, mask=255.255.255.0, gw=192.168.30.1
         host=192.168.30.10, domain=, nis-domain=(none)
         bootserver=192.168.30.100, rootserver=192.168.30.100, rootpath=
    VFS: Mounted root (nfs4 filesystem) on device 0:13.
    devtmpfs: mounted
    Freeing unused kernel image (initmem) memory: 1024K
    Run /sbin/init as init process
    Saving 256 bits of non-creditable seed for next boot
    Starting syslogd: OK
    Starting klogd: OK
    Running sysctl: OK
    Populating /dev using udev: udevd[319]: starting version 3.2.14
    random: udevd: uninitialized urandom read (16 bytes read)
    random: udevd: uninitialized urandom read (16 bytes read)
    random: udevd: uninitialized urandom read (16 bytes read)
    udevd[320]: starting eudev-3.2.14
    done
    Starting iptables: OK
    Network already configured, skipping.
    Starting dropbear sshd: OK
    random: crng init done
    random: 2 urandom warning(s) missed due to ratelimiting
    ssh-keygen: generating new host keys: RSA ECDSA ED25519
    Starting sshd: OK
    Load hi_media.ko success.       (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_mmz.ko success.         (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_common.ko success.      (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_pq.ko success.          (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_hdmi.ko success.        (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_vou.ko success.         (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_gpio.ko success.        (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_gpioi2c.ko success.     (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_i2c.ko success.         (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_tde.ko success.         (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_otp.ko success.         (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_demux.ko success.       (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_adec.ko success.        (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_vfmw.ko success.        (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_svdec.ko success.       (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_vpss.ko success.        (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_vdec.ko success.        (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_cipher.ko success.      (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_adsp.ko success.        (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_aiao.ko success.        (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_fb.ko success.          (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load mali.ko success.   (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_ir.ko success.          (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_jpegdec.ko success.     (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_jpegenc.ko success.     (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_png.ko success.         (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_advca.ko success.       (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_venc.ko success.        (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_aenc.ko success.        (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_keyled.ko success.      (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_vi.ko success.          (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    Load hi_pmoc.ko success.        (SDK_VERSION:[HiSTBLinuxV100R005C09SPC090_20231228])
    ehci-platform: EHCI generic platform driver
    ehci-platform f9890000.ehci: EHCI Host Controller
    ehci-platform f9890000.ehci: new USB bus registered, assigned bus number 1
    ehci-platform f9890000.ehci: irq 32, io mem 0xf9890000
    ehci-platform f9890000.ehci: USB 2.0 started, EHCI 1.00
    hub 1-0:1.0: USB hub found
    hub 1-0:1.0: 2 ports detected
    ehci-platform f9930000.ehci: EHCI Host Controller
    ehci-platform f9930000.ehci: new USB bus registered, assigned bus number 2
    ehci-platform f9930000.ehci: irq 33, io mem 0xf9930000
    ehci-platform f9930000.ehci: USB 2.0 started, EHCI 1.00
    hub 2-0:1.0: USB hub found
    hub 2-0:1.0: 1 port detected
    ohci-platform: OHCI generic platform driver
    ohci-platform f9880000.ohci: Generic Platform OHCI controller
    ohci-platform f9880000.ohci: new USB bus registered, assigned bus number 3
    ohci-platform f9880000.ohci: irq 34, io mem 0xf9880000
    hub 3-0:1.0: USB hub found
    hub 3-0:1.0: 2 ports detected
    ohci-platform f9920000.ohci: Generic Platform OHCI controller
    ohci-platform f9920000.ohci: new USB bus registered, assigned bus number 4
    ohci-platform f9920000.ohci: irq 35, io mem 0xf9920000
    hub 4-0:1.0: USB hub found
    hub 4-0:1.0: 1 port detected
    xhci-hcd f98a0000.xhci: xHCI Host Controller
    xhci-hcd f98a0000.xhci: new USB bus registered, assigned bus number 5
    xhci-hcd f98a0000.xhci: hcc params 0x0220f06c hci version 0x100 quirks 0x0000000000010010
    xhci-hcd f98a0000.xhci: irq 36, io mem 0xf98a0000
    xhci-hcd f98a0000.xhci: xHCI Host Controller
    xhci-hcd f98a0000.xhci: new USB bus registered, assigned bus number 6
    xhci-hcd f98a0000.xhci: Host supports USB 3.0 SuperSpeed
    hub 5-0:1.0: USB hub found
    hub 5-0:1.0: 1 port detected
    usb usb6: We don't know the algorithms for LPM for this host, disabling LPM.
    hub 6-0:1.0: USB hub found
    hub 6-0:1.0: 1 port detected
    /
    Welcome to histb-3798mv100
    histb login: root
    Password:
    Welcome to histb-3798mv100
    root@histb:~#
    

## Support

若本文对你的学习与工作有所帮助、启发，欢迎支持！  
[SupportQR](../Support/SupportQR.md)
