title: 安装php-fpm——源码安装php
tags:
  - linux
  - PHP
  - 源码
id: 1201
categories:
  - 
date: 2014-01-09 22:56:43
---

**准备**

安装php-fpm，需要使用一些rpm包需要从第三方源获取，安装第三方源，可以参考：[安装repoforge第三方源](http://ilidong.com/html/1185.html "安装repoforge第三方yum源")

**下载最新php源码**

国内可以选择（这个速度要快些）

	wget http://cn2.php.net/get/php-5.5.7.tar.gz/from/this/mirror

**安装**

安装一些软件包(编译php时所需要的，这里是提前安装，这里不安装，编译时，系统提示时安装也可)

	yum install –y libxml2-devel libjpeg-devel libpng-devel freetype-devel openssl-devel libcurl-devel libmcrypt-devel mysql mysql-server mysql-devel

解压php源代码

	tar –xvf  php

运行./configure 配置（需要添加一些参数）

{% codeblock %}	./configure --prefix=/usr/local/php --with-config-file-path=/usr/local/php/etc --with-mysql=/usr/ --with-iconv-dir --with-freetype-dir --with-jpeg-dir --with-png-dir --with-zlib --with-libxml-dir=/usr --enable-xml --disable-rpath --enable-discard-path --enable-magic-quotes --enable-safe-mode --enable-bcmath --enable-shmop --enable-syvsem --enable-inline-optimization --with-curl --with-curlwrappers --enable-mbregex --enable-fastsgi --enable-fpm --enable-force-cgi-redirect --enable-mbstring --with-mcrypt --enable-ftp --with-gd --enable-gd-native-ttf --with-openssl --with-mhash -enable-pcntl --enable-sockets --with-xmlrpc --enable-zip -enable-soap --enable-pear --with-gettext -with-mime-magic
{% endcodeblock %}
编译make

`make install` 安装

安装目录为`/usr/local/php`

**配置php**

配置文件在

	/usr/local/php/etc

	cp (php源码文件夹)php.ini-production /usr/local/php/etc/php.ini

	cp php-fpm.conf.default php-fpm.conf

**启动php-fpm**

在目录sbin/ 运行./php-fpm

没有任何报错说明服务成功启动

	ps aux|grep php      //可以查看到php-fpm进程

	netstat –tupln   //可以看到监听有127.0.0.1:9000 的服务

到此php-fpm安装成功

参考视频教程 ：[itercast视频教程](http://itercast.com/lecture/151)