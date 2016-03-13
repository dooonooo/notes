title: Oracle VM VirtualBox不能安装64位系统
tags:
  - VirtualBox
id: 1565
categories:
  - 电脑网络
date: 2014-09-02 11:03:55
---

今天在公司用一台新的电脑，准备使用虚拟机安装Linux系统，下载Oracle VM VirtualBox，准备安装的时候发现如下情况

[undefined](http://ilidong.com/wp-content/uploads/2014/09/1565-1.png)居然不能使用64位系统，全是32位系统，搜索了一下，发现<span style="line-height: 1.714285714; font-size: 1rem;">安装64位需要主板和CPU支持，在BIOS中查看是否有virtualization选项是否开启，开启后vbox就可以安装64位系统了。[undefined](http://ilidong.com/wp-content/uploads/2014/09/1565-2.jpg)</span>

<span style="line-height: 1.714285714; font-size: 1rem;">之前我的电脑可以使用，应该是我的那台电脑默认开启了。</span>