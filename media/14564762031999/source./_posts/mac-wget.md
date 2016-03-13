title: 给Mac添加wget功能
date: 2015-08-23 22:01:25
tags:
- Mac小技巧
- wget
---
wget是个好工具，但是Mac上本身没有这个工具
![](https://dn-lidongim.qbox.me/15-8-23/92308559.jpg)
下面我们给Mac添加wget功能
<!--more-->
1. 打开https://ftp.gnu.org/gnu/wget/选择下载最新版wget（我下载的是tar.gz版）
![](https://dn-lidongim.qbox.me/15-8-23/11473128.jpg)

2. 找到下载的文件，双击解压文件得到一个文件夹，在终端中打开进入到该文件夹

3. 输入 `./configure --with-ssl=openssl`后按下回车并等它安装完成

4. 输入 make 后同样按下回车

5. 然后输入代码`sudo make install`（有可能需要输入你的Mac密码）就安装完成啦！
	
6. 现在测试一下是否安装完成，输入 `wget http://www.lidong.im/` ，如果正常执行就说明成功啦！（如果不行则重新从头做一次）


PS：

其实Mac也自带了一个Curl同样也可以下载网页，用法：
```curl -O [文件的URL]```

