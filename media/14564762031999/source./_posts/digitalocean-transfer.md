title: Digitalocean地区迁移
date: 2015-10-26 12:34:15
categories:
tags:
- digitalocean
- 迁移
---
在网上看到很多说San Francisco速度快一些，而我用的是Singapore今天测速看了一下，发现San Francisco确实是更快一些，延迟也会更低一些
<!--more-->
### 1.关机
![][image-1]
### 2.设置快照(snapshots)
Take a Snapshot
### 3.迁移
将快照发送的sfo（根据快照的大小，可能需要一些时间）
![][image-2]
### 4.重装
也就是重新买一个，在选择镜像(select image)的时候,选择刚刚的snapshots
![][image-3]



测速情况
San Francisco：
![][image-4]
Singapore：
![][image-5]

### 速度测试连接
[https://www.digitalocean.com/community/questions/do-you-have-a-speed-test][1]


#### 参考链接
[http://boweihe.me/?p=1369][2]
[http://www.laozuo.org/3907.html][3]

[1]:	https://www.digitalocean.com/community/questions/do-you-have-a-speed-test
[2]:	http://boweihe.me/?p=1369
[3]:	http://www.laozuo.org/3907.html

[image-1]:	http://img3.lidong.me/pic/pic20151026135142pyh8m.png "关机"
[image-2]:	http://img3.lidong.me/pic/pic201510261358360rcf4.png
[image-3]:	http://img3.lidong.me/pic/pic20151026140158f8vjw.png
[image-4]:	http://img3.lidong.me/pic/pic20151026154219qgs3f.png
[image-5]:	http://img3.lidong.me/pic/pic20151026154517jodyn.png

