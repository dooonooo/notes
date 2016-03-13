title: 快速开启HTTP服务器
date: 2015-11-08 22:43:41
categories:
tags:
- HTTP
- note
---

时常需要使用HTTP服务器环境，
今天发现一条命名就可以开启服务器（机器上需要安装有Python）

	$ python -m SimpleHTTPServer 8000
	
8000位端口号，可选，默认是8000，设置成其他比如 8080，8888

另外惊喜的发现，居然可以同时在不同的端口开启HTTP服务器
<!--more-->
	
	

