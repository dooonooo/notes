title: '【linux学习笔记】解决问题E: 无法获得锁 /var/lib/dpkg/lock - open'
tags:
  - linux
id: 68
categories:
  - 电脑网络
date: 2013-11-01 08:24:48
---

<span style="font-size: medium;">ERROR:
“E: 无法获得锁 /var/lib/dpkg/lock - open (11: 资源暂时不可用)
E: 无法锁定管理目录(/var/lib/dpkg/)，是否有其他进程正占用它？”
解决办法如下：
1.   终端输入 ps  -aux ，列出进程。找到含有apt‘-get或者wget的进程，
直接sudo kill PID。解决。
2.   强制解锁,命令
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock</span>