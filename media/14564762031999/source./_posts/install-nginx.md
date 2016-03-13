title: lnmp环境搭建——nginx安装
tags:
  - linux
  - nginx
id: 1174
categories:
  - 电脑网络
date: 2014-01-05 22:59:46
---

星期五获得了华为云主机赠送1000元，于是开始对华为云体验兼学习。
虽然有lnmp一键安装包，但是自定义安装，将更加个性化，便于适当取舍。
搭建lnmp建议使用全新的系统。第一次使用的华为云主机当然是是全新的系统啦。
系统配置：
centos 6.3 64bit
安装nginx，确保apache没有安装。若安装了最好卸载。

**安装开发工具软件组**

	yum groupinstall -y “Development Tools”

**下载nginx**
需要到nginx官方网站http://nginx.org下载，

	wget http://nginx.org/download/nginx-1.4.4.tar.gz

解压，tar –xvf nginx-1.4.4.tar.gz
运行./configure生成makefile
使用make编译
make install安装
若一切正常，nginx到此就安装成功了。

nginx默认安装在 /usr/local/nginx/目录
配置文件保存在/usr/local/nginx/conf/目录中

**启动nginx**

	/usr/local/nginx/sbin/nginx

**注：**若启动nginx提示，error while loading shared libraries: libpcre.so.1: cannot open shared object file: No such file or directory，这意思是找不到libpcre.so.1这个模块，于是启动失败。
如果是32位系统
运行

	ln -s /usr/local/lib/libpcre.so.1 /lib

如果是64位系统
运行

	ln -s /usr/local/lib/libpcre.so.1 /lib64

再启动nginx就OK了

	/usr/local/ nginx/sbin/nginx

参考：itercast.com视频学习