title: iOS免越狱使用goagent翻墙
tags:
  - goagent
  - ios
  - 翻墙
id: 1067
categories:
  - 电脑网络
date: 2013-12-27 18:56:32
---

之前[电脑端使用goagent翻墙](http://ilidong.com/html/612.html "GAE+chrome 翻墙教程")，现在在iOS设备也使用goagent，而且是不用越狱的噢，如果早知道，就不用急着去越狱，直接用这方法翻墙了。 条件：

1.  ios设备(iPad,iPhone)
2.  电脑一台
3.  无线网络
4.  Goagent文件包
<!--more-->将将ios设备和电脑都连接到无线网络。
**电脑端**
修改goagent的local目录下proxy.ini监听ip 修改前
{% blockquote %}
		[listen]
		ip =127.0.0.1
		port = 8087
		visible = 1
		debuginfo = 0

{% endblockquote %}
修改后

{% blockquote %}[listen]
ip = 0.0.0.0
port = 8087
visible = 1
debuginfo = 0]
{% endblockquote %}

查看电脑的IP地址：比如我的是192.168.0.100
**iOS设备端**
修改无线网络设置
设置HTTP代理为手动，服务器与电脑端的地址相同我的就是192.168.0.100，端口为8087

[undefined](http://ilidong.com/wp-content/uploads/2013/12/ipad无线网络设置修改.png)
设置完成后，在电脑端启动goagent程序，iOS端就可以翻墙啦。