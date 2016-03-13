title: 常用命令
tags:
  - linux
  - 命令
id: 954
categories:
  - 电脑网络
date: 2013-11-23 22:59:52
---

**日期时间**

命令date用以查看设置当前系统日期时间
格式化显示时间：+%Y--%m--%d(Y、m、d、--可以更换)
命令hwclock（clock）用以查看硬件时钟时间
命令cal用以查看日历
命令uptime用以查看系统运行时间，登录用户数量，平均负载（1分钟，5分钟，15分钟）
<!--more-->

**输出、查看**
命令echo用以显示输入的内容
命令cat用以显示文件内容
命令more用以翻页显示文件内容（只能向下翻页，空格翻页）
命令less用以翻页显示文件内容（可以上下翻页，上下方向键或pageup、pagedown翻页，按q退出查询）
命令head用以显示文件的头几行（默认10行）
-n 指定显示行数
命令tail用以显示文件的末尾几行（默认10行）
-n 指定显示行数
-f 追踪显示文件更新（一般用于查看日志，命令不会退出而是持续显示新加入的内容）

**查看硬件信息**
命令lspci用以查看PCI设备
-v 查看详细信息
命令lsusb用以查看USB设备
-v 查看详细信息
命令lsmod用以查看加载的模块（驱动）

**关机、重启**
命令shutdoun用以关闭、重启计算机
shutdown [关机、重启]时间
-h 关闭计算机
-r 重启计算机
如：
立即关机：shutdown -h now
10分钟后关机：shutdown -h +10
23：00关机：shutdown -h 23：00
命令poweroff用以立即关机计算机
命令reboot用以立即重启计算机

**归档、压缩**
命令zip用以压缩文件
zip 压缩后的文件名 要压缩的文件
命令unzip用以解压文件
unzip 压缩文件
命令gzip用以压缩文件
命令tar用以归档文件

*   tar -cvf 要归档的文件 （创建归档）
*   tar -xvf 要释放归档文件 (解开归档)
*   tar -cvzf 要归档并压缩文件 （归档并压缩文件，文件后缀：.tar.gz）


**查找**
命令locate用以快速查找文件、文件夹
此命令需要预先建立数据库，数据库默认每天更新一次
可用update命令手工建立、更新数据库
命令find用以高级查找文件、文件夹
find 查找位置 查找参数
如：

find . -name*aabb*
find / -name*.conf 以.conf
find /-perm 777 查找权限是
find /-type d
find /-type l 查找链接（快捷方式）
find .-name“a*” -exec ls -l ｛｝\; 查找以a开头的文件（ -exec ...｛｝\;固定格式）并作为参数传递给...执行
查找条件：
-name 基于文件名
-perm 基于权限
-user 查找属于某个用户的文件
-group 查找属于某个组的文件
-ctime 基于文件最后修改时间
-type 基于类型
-size 基于大小