title: Windows平台文件md5查看方法
tags:
  - md5
  - 软件
id: 1245
categories:
  - 电脑网络
date: 2014-01-14 15:06:28
---

有时想要查看文件的md5值，与文件提供的md5值比对，确认文件是否被损坏或被篡改了。但是window没有自带的文件md5值查看工具。那我们该怎么去查看呢？

**方法一**：windows虽然没自带文件md5值查看工具，但是微软还是提供工具的，需要我们自己去下载，[点我去下载](http://ilidong.com/ul57)。将下载的文件与要查看md5值文件放在同一文件夹中，运行命令提示符（cmd），切换到对应文件夹，输入fciv 文件名，如：fciv ilidong.zip ，即可得出一个32位数字或字母组成的字符，这就是该文件的md5值。

**方法二**：下载nirsoft的 hash_my_files软件进行查看，下载地址：[官网下载](http://ilidong.com/xsye) [本站下载](http://ilidong.com/download/software/hashmyfiles.zip)