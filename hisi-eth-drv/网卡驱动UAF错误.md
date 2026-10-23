## 背景介绍

        HiSTBLinuxV100R005C00SPC041B020版本的SDK是基于linux-3.18内核，比较旧。基于hi3798mv100硬件平台，
    把HiSTBLinuxV100R005C00SPC041B020版本的驱动移植到linux-5.15内核上。使用buildroot创建工具链，和根文件系统。
    全部代码的移植工作基本完成，编译通过。到了将代码放到目标硬件实际运行的阶段。
        调试阶段使用NFS挂载根文件系统，网卡eth0驱动是基础。
    

## 一、问题描述

    1、启动日志：
    		[   15.277610] ==================================================================
    		[   15.284889] BUG: KASAN: slab-out-of-bounds in hieth_net_hard_start_xmit+0x1ec/0x328
    		[   15.292594] Read of size 4 at addr 859a0e90 by task kworker/u9:1/283
    		[   15.300469] CPU: 2 PID: 283 Comm: kworker/u9:1 Not tainted 5.15.134_s40 #394
    		[   15.307541] Hardware name: Hi3798MX-Platform
    		[   15.311827] Workqueue: xprtiod xs_stream_data_receive_workfn
    		[   15.317538] Backtrace:
    					...... 调用栈省略，整理后给出 ......
    		[   15.773604] bfa0:                                     00000000 00000000 00000000 00000000
    		[   15.781807] bfc0: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
    		[   15.790006] bfe0: 00000000 00000000 00000000 00000000 00000013 00000000
    		[   15.796648]  r10:00000000 r9:00000000 r8:00000000 r7:00000000 r6:00000000 r5:801625e0
    		[   15.804489]  r4:83b11940
    					...... 分配栈省略，整理后给出 ......
    		[   15.873560] The buggy address belongs to the object at 859a0e40
    		[   15.873560]  which belongs to the cache skbuff_head_cache of size 176
    		[   15.885919] The buggy address is located 80 bytes inside of
    		[   15.885919]  176-byte region [859a0e40, 859a0ef0)
    		[   15.896196] The buggy address belongs to the page:
    		[   15.900997] page:a63e1400 refcount:1 mapcount:0 mapping:00000000 index:0x0 pfn:0x59a0
    		[   15.908848] head:a63e1400 order:1 compound_mapcount:0
    		[   15.913912] flags: 0x10200(slab|head|zone=0)
    		[   15.918229] raw: 00010200 a63dd8c4 a63dd804 81a7e740 00000000 00120012 ffffffff 00000001
    		[   15.926331] page dumped because: kasan: bad access detected
    		[   15.931912]
    		[   15.933408] Memory state around the buggy address:
    		[   15.938211]  859a0d80: fc fc fc fc fc fc fc fc fc fc fc fc fc fc fc fc
    		[   15.944755]  859a0e00: fc fc fc fc fc fc fc fc fc fc fc fc fc fc fc fc
    		[   15.951296] >859a0e80: fc fc fc fc fc fc fc fc fc fc fc fc fc fc fc fc
    		[   15.957832]                  ^
    		[   15.960899]  859a0f00: fc fc fc fc fc fc fc fc fc fc fc fc fc fc fc fc
    		[   15.967441]  859a0f80: fc fc fc fc fc fc fc fc fc fc fc fc fc fc fc fc
    		[   15.973978] ==================================================================
    		[   15.981207] Disabling lock debugging due to kernel taint
    
    2、整理后的调用栈：
    	dump_backtrace  -> show_stack    -> dump_stack_lvl   -> print_address_description        
    													-> kasan_report            # 检测到非法访问
    											        -> __asan_load4            # 实际触发的是 4 字节读取
    							    -> hieth_net_hard_start_xmit[<8081c9b4>] + 0x1ec   # 实际发生错误的函数
        -> dev_hard_start_xmit -> sch_direct_xmit -> __dev_queue_xmit -> dev_queue_xmit -> ip_finish_output2 
        -> _ip_finish_output -> ip_output  -> __ip_queue_xmit -> ip_queue_xmit -> __tcp_transmit_skb 
        -> __tcp_send_ack.part.0 -> tcp_send_ack -> tcp_cleanup_rbuf   -> tcp_recvmsg_locked -> tcp_recvmsg 
        -> inet_recvmsg -> sock_recvmsg -> xs_stream_data_receive_workfn -> process_one_work 
        -> worker_thread -> kthread -> ret_from_fork
    
    3、整理后的分配栈：
    	__kasan_slab_alloc -> kmem_cache_alloc
    					 -> __alloc_skb                    # 分配 socket 缓冲区
        -> __tcp_send_ack.part.0 -> tcp_send_ack -> tcp_cleanup_rbuf -> tcp_recvmsg_locked -> tcp_recvmsg -> inet_recvmsg 
        -> sock_recvmsg -> xs_stream_data_receive_workfn -> process_one_work -> worker_thread -> kthread -> ret_from_fork
    
    4、出错概率：
    	并不是每一次启动一定出错，但是有比较高的概率，3到5次重启能见到一次。
    

## 二、初步分析排查：

    1、关键信息：
    	1）、出错变量名和地址：
    	     已分配内存块大小176字节，范围（0x859a0e40, 0x859a0ef0）出错的地址位于首址偏移80处，即0x859a0e40+0x50 = 
    	     0x859a0e90。该内存块是 `struct sk_buff` 对象，由 `__alloc_skb()` 分配，来源于 `skbuff_head_cache` 缓存。
    	2）、出错函数名：
    		出错的函数名hieth_net_hard_start_xmit，在它首址<0x80aa034c> + 0x1ec处。
    	3）、出错的类型：
    		错误日志标题是 `slab-out-of-bounds`。但“shadow memory 对应字节为 `fc`，表示该地址所在的 kmalloc 对象已被释放”。
    2、查看源码：
    	 grep -r 'hieth_net_hard_start_xmit' ./
    		./hi3798mveth/hieth.c:         static int hieth_net_hard_start_xmit(struct sk_buff *skb,
    	sed -n '642,645p;650,656p;671,681p' ./hi3798mveth/hieth.c
    		static int hieth_net_hard_start_xmit(struct sk_buff *skb,struct net_device *dev)
    		{
    		        struct hieth_netdev_priv *priv = netdev_priv(dev);
    		        if (!hieth_hw_xmitq_ready(priv)) {
    		                priv->stats.tx_dropped++;
    		                netif_stop_queue(dev);
    		                hieth_irq_enable(priv,
    		                                UD_BIT_NAME(HIETH_GLB_IRQ_INT_TXQUE_RDY));
    		                return NETDEV_TX_BUSY;
    		        }
    		        dma_map_single(priv->dev, skb->data, skb->len, DMA_TO_DEVICE);
    		        hieth_xmit_real_send(priv, skb);
    		        //dev->trans_start = jiffies;           // deleted by huxm 20260114
    		        netif_trans_update(dev);                        // replaced by huxm 20260114
    		        priv->stats.tx_packets++;
    		        priv->stats.tx_bytes += skb->len;
    		        return NETDEV_TX_OK;
    		}
    3、反汇编确认报错偏移:
    	出错地址 = 函数入口 + 偏移 = 8081c9b4 + 0x1ec = 8081cba0
    	./arm-linux-objdump -d  ./out/.../vmlinux | grep -A 130 "<hieth_net_hard_start_xmit>:" | grep -C3 '8081cba0:'
    			8081cb94:       e1a00007        mov     r0, r7
    			8081cb98:       e59465a4        ldr     r6, [r4, #1444] @ 0x5a4
    			8081cb9c:       ebea6012        bl      802b4bec <asan_load4>
    			8081cba0:       e5953050        ldr     r3, [r5, #80]   @ 0x50
    			8081cba4:       e3a00000        mov     r0, #0
    			8081cba8:       e0833006        add     r3, r3, r6
    			8081cbac:       e58435a4        str     r3, [r4, #1444] @ 0x5a4
    	8081cba0:       e5953050        ldr     r3, [r5, #80]   @ 0x50     这条汇编指令就是从 `r5`（即 `skb` 指针）偏移 
    	`0x50 = 80` 字节处读取 4 字节。结合 KASAN 报告“Read of size 4 at addr 859a0e90”，对象起始是 `0x859a0e40`，
    	`0x859a0e90 - 0x859a0e40 = 0x50`，完全吻合。所以出错点就是：priv->stats.tx_bytes += skb->len。
    4、错误定性：
    	错误日志标题明确是 `slab-out-of-bounds`，但读 `skb` 对象内部偏移 80 字节并未超出对象范围（对象大小 176 字节），且 shadow 
    	memory 状态是 `fc`（已释放）。这更像是 `use-after-free`，而非 `slab-out-of-bounds`。
    

## 三、深入分析原因

    1、分析相关源码：
    出错点：`hieth_net_hard_start_xmit` 中执行 `priv->stats.tx_bytes += skb->len;` 时，`skb` 已被释放，属于典型的 
    use-after-free。
    发送路径梳理：
    	a. 网络协议栈调用 `hieth_net_hard_start_xmit`，将待发送的 `skb` 传递给驱动。
    	b. 驱动调用 `hieth_xmit_real_send`，将 `skb` 挂入发送队列，启动硬件发送动作，然后函数返回。
    	c. 发送动作完成后，硬件产生中断，触发 `hieth_net_isr` 中断服务程序。
    	d. 中断服务程序调用 `hieth_net_isr_proc`，在其中调用 `napi_schedule(&priv->napi)` 调度 NAPI。
    	e. 由于 `hieth_platdev_probe_port` 中已调用 `netif_napi_add` 注册了 `hieth_poll` 作为 NAPI 的回调函数，因此在软中断
    	上下文中，	`hieth_poll` 会被执行，并作为最终的处理函数，处理发送完成事件，很可能在这里释放 `skb`。
    
    2、定位skb释放点：
    	sed -n "1016,1030p" ./hi3798mveth/hieth.c
    		static int hieth_poll(struct napi_struct *napi, int budget)	{
    		        struct hieth_netdev_priv *priv = NULL;
    		        unsigned int work_done = 0;
    		        priv= container_of(napi, struct hieth_netdev_priv, napi);
    		        hieth_xmit_release_skb(priv);
    		        hieth_clean_rx(priv, &work_done, budget);
    		        ..... 省略 ......
    		        return work_done;
    		}
    	hieth_xmit_release_skb(priv)内部调用dev_kfree_skb_any(skb);释放了skb导致了错误。
    

## 四、修复策略：

    1、修复策略示意。
    把启动硬件发送数据放在更新数据之后，返回之前。并且在更新priv->stats上锁，更新完成后解锁。如下面所示：
    sed -n '642,644p;672,682p' ./hi3798mveth/hieth.c
    static int hieth_net_hard_start_xmit(struct sk_buff *skb,struct net_device *dev){
    	// hieth_xmit_real_send(priv, skb); // moved to after tx_bytes update (which uses skb->len) (by huxm 20260830)
    	//dev->trans_start = jiffies;       // removed from active code (by huxm 20260114)
    	netif_trans_update(dev);            // replaces the old dev->trans_start = jiffies (by huxm 20260114)
    	hieth_local_lock(priv);// Acquire lock to protect tx statistics updates from concurrent access(by huxm 20260830)
    	priv->stats.tx_packets++;
    	priv->stats.tx_bytes += skb->len;
    	hieth_local_unlock(priv);    // Release lock after tx statistics updates are completed(by huxm 20260830)
    	hieth_xmit_real_send(priv, skb); // relocated to after tx_bytes update (which uses skb->len) (by huxm 20260830)
    	return NETDEV_TX_OK;
    }
    
    2、修复策略的理论依据：
    hieth_xmit_real_send 内部已持有 hieth_local_lock(priv)，而 hieth_poll 在释放 skb 时也需要同一把锁，因此发送路径与释放路径是互
    斥的。中断中仅触发 NAPI，不加锁，锁只用于 softirq 的 poll 处理。
    在 hieth_net_hard_start_xmit 的另一个分支中，当 hieth_hw_xmitq_ready() 返回 false 时，驱动既不会调用 hieth_xmit_real_send，
    也不会	将 skb 交给硬件，因此不存在“硬件提前完成并释放 skb”的风险。NETDEV_TX_BUSY 的语义是驱动暂时无法接收该 skb，要求内核协
    议栈稍后重试；
    __dev_queue_xmit 收到该返回值后会把 skb 重新入队，不会释放它，所以这个分支本身不会引发 use-after-free 问题。
    如果 netif_stop_queue 停止队列后，没有任何路径调用 netif_wake_queue，发送确实会永久停住，表现为“忙等”。但驱动注册了 
    HIETH_GLB_IRQ_INT_TXQUE_RDY 中断，当队列重新可写时会触发中断并重新启动队列，因此正常情况下不会发生死锁。
    

## 五、修复后测试：

    修复后连续执行10次重启，再也没有出现KASAN报错。
    

## Support

若本文对你的学习与工作有所帮助、启发，欢迎支持！  
[SupportQR](../Support/SupportQR.md)

## 其它细节
