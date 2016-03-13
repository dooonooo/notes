title: 禁止统计代码统计自己
tags:
  - PHP
  - web
id: 1045
categories:
  - 电脑网络
date: 2013-12-25 22:28:46
---

参考露兜博客，稍加改动
作为网站的管理者，每天要打开我的网站无数次。给网站安装了统计代码后，如果自己的产生的这些流量也都被统计工具统计进去，势必影响统计结果，违背统计的初衷。
如何避免这种情况：
1\. wordpress不统计登录用户
如果wordpress网站是单个用户的，不统计登录用户的流量，就是不统计自己访问数据了，一般我们都将统计代码放在footer.php中，那现在用文本编辑器打开你的footer.php，找到你的统计代码，将其改成：

	<?php global $user_ID; if (!$user_ID) : ?> 
	这里替换成统计代码 
	<?php endif; ?>

这样当没有用户登录的情况下，页面输出统计代码；用户登录的情况下页面，不会输出统计代码。
<!--more-->2\. WordPress不统计特定登录用户
在WordPress博客系统中，已为每位用户分配一个用户ID，如果不想统计ID为5的用户访问信息，可以将统计代码改成：

	[<?php global $user_ID; if ( 5 != $user_ID) : ?> 
	这里替换成统计代码 
	<?php endif; ?>

用户ID可照此方法获取

	WordPress后台 - 用户，这里每个用户名都是类似以下的超链接: http://example/wp-admin/user-edit.php?user_id=5&wp_http_referer=/wp-admin/users.php 那么该用户的ID就是5

3.如何不统计特定IP的用户
如果你使用的是固定IP或者固定的IP段，那这个问题就更好办了，不统计你指定的IP或IP段即可。

	<?php $iipp = ‘ ’ . $_SERVER[“REMOTE_ADDR”]; // 将以下 192.168.2.1 改成你的IP或IP地址段 if ( strpos($iipp,‘192.168.2.1’) === false ) : ?> 
	这里替换成统计代码 
	<?php endif; ?>

	<?php $iipp = ‘ ’ . $_SERVER[“REMOTE_ADDR”];


// 同理你可以增加排除IP的个数

	 if ( strpos($iipp,‘192.168.2.1’) === false || strpos($iipp,‘192.168.2.2’) === false) : ?> 这里替换成统计代码 <?php endif; ?>