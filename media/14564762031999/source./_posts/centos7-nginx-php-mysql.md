title: CentOS7.0编译安装nginx1.9.8、php5.6(php-fpm)
date: 2015-12-09 18:44:32
categories:
tags:
- centos
- nginx
- php
---

折腾好久，终于完整的整理了Nginx＋PHP的安装
安装顺序最好是先安装PHP，再安装Nginx
<!--more-->
## 1.安装php

`wget http://cn2.php.net/distributions/php-5.6.16.tar.gz`
`tar -xvf php-5.6.16.tar.gz`
`cd php-5.6.16/`

` ./configure --prefix=/usr/local/php  --enable-inline-optimization --disable-debug --disable-rpath --enable-shared --enable-opcache --enable-fpm --with-fpm-user=www --with-fpm-group=www --with-mysql=mysqlnd --with-mysqli=mysqlnd --with-pdo-mysql=mysqlnd --with-gettext --enable-mbstring --with-iconv --with-mcrypt --with-mhash --with-openssl --enable-bcmath --enable-soap --with-libxml-dir --enable-pcntl --enable-shmop --enable-sysvmsg --enable-sysvsem --enable-sysvshm --enable-sockets --with-curl --with-zlib --enable-zip --with-bz2 --with-readline --without-sqlite3 --without-pdo-sqlite --with-pear`

`make`
`sudo make install`

安装完成的截图

![安装完成](https://dn-blogme.qbox.me/15-12-14/62005590.jpg)

设置php-fpm配置文件
`cp /usr/local/php/etc/php-fpm.conf.default /usr/local/php/etc/php-fpm.conf`

启动php-fpm
`sudo /usr/local/php/sbin/php-fpm`


### 编译过程可能出现的报错情况

configure: error: xml2-config not found. Please check your libxml2 installation.
`sudo yum install -y libxml2-devel`

configure: error: Cannot find OpenSSL's <evp.h>
`sudo yum install -y openssl-devel`

configure: error: Please reinstall the BZip2 distribution
`sudo yum install -y bzip2-devel`

configure: error: Please reinstall the libcurl distribution -
    easy.h should be in <curl-dir>/include/curl/
`sudo yum install -y libcurl-devel`

configure: error: mcrypt.h not found. Please reinstall libmcrypt.
libmcrypt在官方yum源中没有，需要手动编译安装可以到sourceforge下载
http://sourceforge.net/projects/mcrypt/files/Libmcrypt/ 
`wget http://downloads.sourceforge.net/project/mcrypt/Libmcrypt/2.5.8/libmcrypt-2.5.8.tar.gz`
`tar -xvf libmcrypypt-2.5.8.tar.gz`
`./configure`
`make `
`sudo make install`

configure: error: Don't know how to define struct flock on this system, set --enable-opcache=no
编辑 /etc/ld.so.conf.d/local.conf文件，加入/usr/local/lib内容
`sudo vi /etc/ld.so.conf.d/local.conf`
`/usr/local/lib`
`sudo ldconfig`

configure: error: Please reinstall readline - I cannot find readline.h
`sudo yum install -y readline-devel`

PS：一次全部安装上述依赖
`sudo yum install -y libxml2-devel openssl-devel bzip2-devel libcurl-devel readline-devel`



## 2.安装nginx
`wget http://nginx.org/download/nginx-1.9.8.tar.gz`
解压
`tar -xvf nginx-1.9.8.tar.gz`
`cd nginx-1.9.8.tar.gz`
`./configure`
`make`
`sudo make install`

修改配置文件以支持php-fpm
`sudo  vi /usr/local/nginx/conf/nginx.conf`

其中server段增加如下配置，注意标红内容配置，否则会出现No input file specified.错误
	
	location ~ \.php$ {
            root           html;
            fastcgi_pass   127.0.0.1:9000;
            fastcgi_index  index.php;
            #修改下面字段，否则会出现No input file specified.错误
            fastcgi_param  SCRIPT_FILENAME    $document_root$fastcgi_script_name;
            include        fastcgi_params;
        }

启动nginx
`sudo /usr/local/nginx/sbin/nginx`


PS：这里是nginx编译完成的信息图，在这里可以看到nginx的路径，配置文件位置及其它一些有用信息
![编译完成](https://dn-blogme.qbox.me/15-12-14/7981235.jpg)

### 编译过程可能出现的报错情况

./configure: error: the HTTP rewrite module requires the PCRE library.

`sudo yum -y install pcre-devel`

./configure: error: the HTTP gzip module requires the zlib library.

`sudo yum -y install zlib-devel`






