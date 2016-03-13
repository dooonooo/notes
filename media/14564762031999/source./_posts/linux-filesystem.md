title: linux文件系统
tags:
  - linux
  - 文件系统
id: 993
categories:
  - 电脑网络
date: 2013-12-01 23:37:55
---

**linux文件系统**

操作系统通过文件系统管理文件及数据，磁盘或分区需要文件系统之后才能够为操作系统使用，创建文件an系统的过程又称为格式化。

*   没有文件系统的设备又称为裸（raw）设备
*   常见的文件系统有fat32，NTFS、ext2、ext3、ext4、xfs、HFS等
*   文件系统之间的区别：日志、支持的分区大小、支持单个文件大小、性能等
windows下的主流文件系统：NTFS

linux下主流文件系统：ext3、ext4

**<!--more-->linux支持的文件系统**

ext2

ext3

ext4

fat（msdos）

vfat

nfs

iso9600

proc

gfs

......

**mke2fs**

命令mke2fs用以创建文件系统

mke2fs -t ext4/dev/sda3

常用的参数：

-b  blocksize   指定文件系统块大小

-c     建立文件系统时检查坏损块

-L     指定卷标

-j     建立文件系统日志（ext3、ext4默认带日志）

**mkfs**

命令mkfs也可用于创建文件系统，相较于mke2fs简单，但是支持的参数较少，不能进行精细化的控制。

*   mkfs.ext3 /dev/sda3
*   mkfs.ext4 /dev/sda3
*   mkfs.vfat /dev/sda3
**dumpe2fs**

命令dumpe2fs 可以用来查看分区的文件系统信息

dumpe2fs /dev/sdb2

**journal日志**

带日志的文件系统（ext3、ext4）拥有较强的稳定性，在出现错误时可以进行恢复。

使用带日志的文件系统，文件系统会使用一个叫做“两阶段提交”的方式进行磁盘操作，当进行磁盘操作时，文件系统进行如下操作：

1.  文件系统将准备执行的事务的具体内容写入日志
2.  文件系统进行操作
3.  操作成功后，将事务的具体内容从日志中删除
这样做的好处：当事务执行的时候如果出现意外（如断电，磁盘故障），可以通过查询日志进行恢复操作。缺点：会丧失一定的性能（额外的日志读写操作）。

**e2label**

命令e2label 可以用以为文件系统添加标签

*   e2label /dev/sda2 显示sda2的系统标签
*   e2label /dev/sda2 LINUX 将sda2的系统标签设置为LINUX (标签一般大写)
**fsck**

命令fsck用以检查并修复损坏的文件系统 (检查、修复，磁盘必须卸载)

fsck /dev/sdb1

*   使用-y参数不提示而直接进行修复
*   默认fsck会自动判断文件系统类型，如果文件系统损坏较为严重，最好使用 -t 参数指定文件系统类型
*   对于识别为文件的损坏数据（文件系统无记录），fsck会将该文件放入lost+found目录
*   系统启动时会对磁盘进行fsck操作