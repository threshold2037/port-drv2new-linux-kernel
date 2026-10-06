# HI3798MV100 Linux Kernel Port Bringup

 > 
 > 海思HI3798MV100平台 Linux‑3.18——>linux-5.15 驱动移植与调试项目

## 项目简介

本项目记录ARMv7平台内核完整移植、硬件驱动bringup全过程，包含启动调通过程、时钟子系统、eMMC、网卡、GPU驱动调试，驱动测试，记录遇到的关键BUG、分析思路、修复方案。

✅ 验证结果：内核完成完整启动，输出bootlog，基础外设(eMMC/网口/GPU)可用。

## 📁 仓库内容说明

1. boot_log/：《[boot log](hisi-validation/boot%20log.md)》内核启动成功串口日志与截图，证明移植启动结果
1. git_history/：《[git history](hisi-validation/git%20history.md)》移植阶段部分git提交历史
1. fix the tag/: 《[fix the tag](hisi-validation/fix%20the%20tag.md)》移植阶段大部分修改历史标记（对比linux-3.18）
1. `docs/`：移植调试文档多篇，记录关键问题定位与修复

* 01 《[booting the kernel](hisi-kernel-boot/booting%20the%20kernel.md)》 内核早期启动问题
* 02  《[CLOCKEVENT时钟驱动](hisi-clk-drv/CLOCKEVENT%E6%97%B6%E9%92%9F%E9%A9%B1%E5%8A%A8.md)》主时钟驱动调试
* 03 《[时钟控制器驱动问题](hisi-clk-drv/%E6%97%B6%E9%92%9F%E6%8E%A7%E5%88%B6%E5%99%A8%E9%A9%B1%E5%8A%A8%E9%97%AE%E9%A2%98.md)》CRG时钟控制器驱动调试
* 04 《[mmcblk设备异常](hisi-emmc-drv/mmcblk%E8%AE%BE%E5%A4%87%E5%BC%82%E5%B8%B8.md)》eMMC驱动异常问题修复
* 05 《[网卡驱动UAF错误](hisi-eth-drv/%E7%BD%91%E5%8D%A1%E9%A9%B1%E5%8A%A8UAF%E9%94%99%E8%AF%AF.md)》网卡驱动UAF(Use‑After‑Free)错误分析与解决
* 06 《[gpu的中断号问题](hisi-gpu-drv/gpu%E7%9A%84%E4%B8%AD%E6%96%AD%E5%8F%B7%E9%97%AE%E9%A2%98.md)》GPU硬件中断号向软件中断号转换。约30个\*.ko驱动的共性问题，以GPU为代表。
* 07 《[gpu的oops问题](hisi-gpu-drv/gpu%E7%9A%84oops%E9%97%AE%E9%A2%98.md)》 OOPS崩溃问题排查
* 08 《[lockdep 环形锁依赖告警](hisi-pm-drv/lockdep%20%E7%8E%AF%E5%BD%A2%E9%94%81%E4%BE%9D%E8%B5%96%E5%91%8A%E8%AD%A6.md)》lock造成的死锁，以它为典型代表。
* 09 《[JPEG格式解码死机](hisi-test-drv/JPEG%E6%A0%BC%E5%BC%8F%E8%A7%A3%E7%A0%81%E6%AD%BB%E6%9C%BA.md)》硬件驱动测试验证记录。所有的硬件驱动测试，以它为典型代表。
* 10 《*LTP 测试报告*》LTP 测试报告。包括几千项测试原始记录子目录和测试报告本身。测试报告对豁免测试项有严谨说明。

 > 
 > 省略其余文档包含设备树、大量移植源适配修改记录

## 关键技术点

* U‑Boot与内核启动链路调试，解析早期boot阶段问题
* CRG时钟寄存器配置，时钟子系统bringup
* eMMC host驱动、设备树适配，驱动异常排错
* Linux内核 Use‑After‑Free 内存错误分析
* linux内核 lockdep 环形锁依赖
* GPU中断资源、Oops堆栈解析，定位内核崩溃
* 设备树(DTS)适配，ARMv7底层驱动调试
* 内存分析工具KASAN使用
* 锁分析工具 lockdep使用
* DMA调试工具使用
* ltrace、strace工具使用
* docker下编译buildroot
* 根文件系统裁剪与工具链修复BUG

## 环境

* SOC：HI3798MV100 ARMv7
* Kernel Version：Linux‑5.15
* 文档编写工具：Obsidian

## 版权声明

本仓库全部内容为记录学习过程文档（Markdown笔记、启动日志、排错记录），无配套源代码。
采用 [CC BY‑NC‑ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/deed.zh)。
若需要源码，联系作者本人。

✅允许：仅GitHub网页端在线浏览；引用内容必须标注本仓库来源。

❌禁止：

1. 批量下载、镜像、完整/部分二次公开分发本仓库文档；
1. 修改、改写本仓库内容对外发布；
1. 一切商业用途。
