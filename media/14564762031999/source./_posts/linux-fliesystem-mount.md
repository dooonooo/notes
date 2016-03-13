title: linux文件系统挂载管理
tags:
  - linux
  - 文件系统
id: 995
categories:
  - 电脑网络
date: 2013-12-01 23:39:31
---

**挂载操作**
磁盘或分区创建文件系统后，需要挂载到一个目录才能使用。
windows或Mac系统会进行自动挂载，一旦创建好文件系统后会自动挂载到系统上，windows上称为C盘、D盘。
linux需要手工进行挂载操作或配置系统进行自动挂载。
一般挂载到 /mnt上（其实挂载到任何地方都可以）

**<!--more-->mount**
在linux中，我们通过mount命令将格式化好的磁盘或分区挂载到一个目录上。
mount /dev/sda3(要挂载的分区) /mnt(挂载点)
常用参数
不带参数的mount命令会显示所有已挂载的文件系统
-t 指定文件系统的类型
-o 指定挂载选项

*   ro，rw 以只读或读写形式挂载，默认是rw
*   sync 代表不使用缓存，而是对所有操作直接写入磁盘
*   async 代表使用缓存，默认是async
*   noatime 代表每次访问文件时不更新文件的访问时间
*   atime 代表每次访问文件时更新文件的访问时间
*   remount 重新挂载文件系统
**umount**

命令umount用以卸载已挂载的文件系统，相当于windows中的弹出
umount 文件系统/挂载点
umount /dev/sda3 ?== ? ? umount/mnt
如果出现device is busy 报错，则表示该文件系统正在被使用，无法卸载，可以使用以下命令查看使用文件系统的进程：
fuser -m /mnt
也可以使用命令lsof查看正在被使用的文件：
lsof /mnt

**自动挂载**
配置文件 /etc/fstab用来定义需要自动挂载的文件系统，fstab中的每一行代表一个挂载配置，格式如下：
<table width="100%" border="1" cellspacing="0" cellpadding="2">
<tbody>
<tr>
<td valign="top">/ect/sda3</td>
<td valign="top">/mnt</td>
<td valign="top">ext4</td>
<td valign="top">defaults</td>
<td valign="top">0 0</td>
</tr>
<tr>
<td valign="top">需要挂载的设备</td>
<td valign="top">挂载点</td>
<td valign="top">文件系统</td>
<td valign="top">挂载选项</td>
<td valign="top">dump、fsck相关选项</td>
</tr>
</tbody>
</table>

*   要挂载的设备也可以使用label来识别，使用label= LINUX取代 /dev/sda3
*   mount -a 命令会挂载所有fstab中定义的自动挂载选项