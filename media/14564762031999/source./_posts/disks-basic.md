title: 磁盘基本概念
tags:
  - linux
  - 磁盘
id: 958
categories:
  - 电脑网络
date: 2013-11-23 23:01:04
---

###基本概念
 cylinder 柱面 
 sector 扇片 
 head 磁头 

###磁盘在LINUX中的表示
 Linux中所有设备都被抽象为一个文件,保存在/dev目录下 
 
 设备名称一般是hd[a-z]或sd[a-z].([a-z]为分区号)，如hda，hdb，sda，sdb；
 
- IDE设备名称是hd[a-z],
- SATA,SCSI,SAS,USB等设备的名称是sd[a-z]。（现在的一般都是sd） 

###分区的概念
 把一个磁盘逻辑的分层几个区，每个区当做独立磁盘，以方便使用管理。 <br>
 不同的分区用：设备名称+分区名称，保存在/dev目录下 

 主流分区机制是MBR和GPT两种 
####MBR 
 MBR是传统的分区机制，应用于绝大多数使用BOIS的PC设备。 

*   MBR支持32bit和64bit系统
*   支持分区数量有限
*   只支持不超过2T的硬盘，超过2T的硬盘将只能使用2T的空间（有第三方的解决方法）
MBR结构

MBR分区<br>

 - 主分区  最多只能创建4个主分区 <br>
 - 扩展分区  一个扩展分区会占用一个主分区位置<br> 
 - 逻辑分区  linux最多支持63个IDE分区和SCSI分区<br> 
 
####GPT
 GPT（GUID Partiton Table）是一个较新的分区机制，解决了MBR的很多的缺点 

*   支持超过2T的磁盘
*   向后兼容MBR
*   必须在支持UEFI的硬件上才能使用
*   必须使用64bit系统
*   MAC、Linux系统都能支持GPT分区格式
*   Windows7 64bit、Windows server2008 64bit支持64GPT