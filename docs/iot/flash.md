# nand flash

## SD NAND

SD NAND产品特点：

小尺寸：6*8mm
容量：1Gb,2Gb,4Gb,8Gb，品质稳定，不同于小容量的白牌厂商（Ink Die）
标准SD接口，即贴即用
高可靠性，为嵌入式设计而生

解决痛点
        相比Micro SD+卡座+打胶方式，产品跌落撞击容易导致接触不良；打胶的方式，时间长了，触点依旧氧化，导致接触不良，Micro SD过炉贴到板子上，卡会爆掉

SD NAND适用范围：
        需要使用SD卡，又不需要拨出的嵌入式产品

  	  	MK 第一代 SD NAND 	MK 第二代 SD NAND 	MK 第三代 SD NAND
SD NAND 	1Gbit 	MSD1GL68S  	MK25V1GL 	MKDV1GCL
SDV128M

2Gbit 	MSD2GL68S  	MK25V2GL 	MKDV2GCL
SDV256M
4Gbit 	MSD4GL68S  	MK25V4GL 	MKDV4GIL
SDV512M
8Gbit 	MSD8GL68D 	MK25V8GL 	MKDV8GIL

[立创商城](https://so.szlcsc.com/global.html?k=SD%2520NAND&hot-key=CL21A106KOQNNNE)

[原诚通](http://www.yct-tec.com/a/chanpinzhongxin/2018/0727/4.html)

[SD NAND 二代 1Gb](http://www.longsto.com/product/32.html)

# FTL

## dhara

NAND flash translation layer for low-memory systems

Dhara is a small flash translation layer designed to be used in
resource-constrained systems for managing NAND flash. It provides a
mutable block interface with standard read and write operations.

[src](https://github.com/dlbeer/dhara)

# fs

## UBIFS

[ubifs](http://www.linux-mtd.infradead.org/doc/ubifs.html)

## yaffs2

## littlefs

A little fail-safe filesystem designed for microcontrollers

https://github.com/ARMmbed/littlefs

[using LittleFs on W25N01GV 1Gb NAND Flash with FreeRTOS](https://github.com/littlefs-project/littlefs/issues/361)

[移植LittleFs](https://www.cnblogs.com/imez/articles/10461715.html)

[LittleFS - 一个高度完整的嵌入式文件系统](https://blog.csdn.net/xk100/article/details/85320749)

[littlefs与sfud串行flash通用驱动建立FreeRTOS文件系统](https://blog.csdn.net/dmjkun/article/details/87215164)

## 参考


# Tools

## nand_programmer

NANDO is open source NAND programmer based on STM32 processor.

https://github.com/bbogush/nand_programmer


# 参考

[MDK Middleware for Devices with Flash File System](https://www.keil.com/pack/doc/mw/FileSystem/html/nand_flash__t_l.html)

[NFTL（nand硬件翻译层）＋ FAT 的应用](https://blog.csdn.net/junllee/article/details/44176837)

[商业 FTL](https://zeeis.com/flash-translation-layer/)

[镁光最新的NFTL](https://download.csdn.net/download/weixin_42444263/11522274?utm_medium=distribute.pc_relevant_download.none-task-download-blogcommendfrombaidu-2.nonecase&depth_1-utm_source=distribute.pc_relevant_download.none-task-download-blogcommendfrombaidu-2.nonecase)

[STM32下FatFs的移植，实现了擦写均衡，坏块管理，硬件ECC，ECC纠错](https://download.csdn.net/download/chatwithyou2008/9694193?utm_medium=distribute.pc_relevant.none-task-download-BlogCommendFromMachineLearnPai2-2.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-download-BlogCommendFromMachineLearnPai2-2.channel_param)

[Linux: Alternative to UBIFS on MLC NAND MLC在linux中不被支持？](https://unix.stackexchange.com/questions/448581/linux-alternative-to-ubifs-on-mlc-nand)

[Winbond W25XXX SPI NAND Flash Driver ](https://github.com/mongoose-os-libs/vfs-dev-w25xxx)

[IM_STM32_External_Devices w25n01g](https://github.com/Igor-Misic/IM_STM32_External_Devices/blob/887825b1aa7996cbc9f991d871fa96f39d8cd23f/Winbond/Src/w25n01g.c)

[f1c100s 128MB W25N01G spi nand调试记录](https://github.com/hcly/f1c100s)
