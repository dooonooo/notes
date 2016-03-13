title: 使用fdisk进行磁盘管理
tags:
  - linux
  - 磁盘管理
id: 961
categories:
  - 电脑网络
date: 2013-11-23 23:04:50
---

**fdisk分区工具**
fdisk是来自IBM的老牌分区工具，支持绝大多数的操作系统，几乎所有的Linux的发行版本都装有fdisk，包括在linux的rescue（救援模式）模式下的依然能够使用。
fdisk是一个基于MBR的分区工具，如果使用GPT，则无法使用fdisk进行分区。

<!--more-->
**fdisk**
fdisk命令只有超级用户（root）权限才能够运行
使用fdisk -l 可以列出所有安装的磁盘及其分区信息
使用fdisk /dev/sda 可以对目标磁盘进行分区操作
分区之后需要使用partprobe命令让内核更新分区信息，否则需要重启才能识别新的分区
/proc/partitions 文件也可用来查看分区信息