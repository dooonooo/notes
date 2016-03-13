title: 在WordPress中使用二级域名发布RSS Feed
tags:
  - wordpress
id: 1087
categories:
  - 电脑网络
  - 网站日志
date: 2013-12-28 20:54:04
---

Feed托管服务国外有Feedburnner，国内有Feedsky。
但是依赖其它的网站的服务貌似都不太可靠，一旦这网站的服务停止，使用该网站服务的网站就不得不停止。所以俺喜欢还是自己把握自己的网站的服务。使用二级域名发布RSS feed的好处还有就是方便管理，也方便记忆，也比较好看。

WordPress 二级域名Feed地址设置方法：

1.  在你域名DNS设置中添加二级域名，feed.xxx.com
2.  在主机后台添加子域名，在cPanel是叫子域（Subdomain）的地方添加二级域名，并指向一个目录，一般系统会指向网站主文件夹/public_html/目录下的同名目录，但是WordPress默认的RSS feed链接格式本来就是xxx.com/feed/（在使用了固定链接的情形下），如果将feed.xxx.com指向/public_html/feed就会产生冲突，所以建议指向/public_html/feeds目录，便于自己记忆。注意：如果系统自动创建了feed目录，需要手工将feed目录删除。
3.  新建一个index.php的文件，文件内容为：

		<?php header(“Content-Type: application/xml; charset=utf-8”) ; @readfile(“//FEED源XML文件的地址//”); ?>

4.  OK，大功告成，等你的域名解析生效之后，访问feed.xxx.com,就可以得到和xxx.com/feed一样的内容了。
欢迎 订阅本站[http://feed.ilidong.com](http://feed.ilidong.com "订阅本站")