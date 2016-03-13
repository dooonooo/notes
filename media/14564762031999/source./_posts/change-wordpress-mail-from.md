title: 修改WordPress邮件通知的发件人
tags:
  - wordprees
id: 1660
categories:
  - 电脑网络
date: 2015-02-01 20:45:13
---

使用新的主机，发现我的WordPress可以不使用插件就可以发送通知邮件了，但是发件人是wordpress，与之前自定义的不一样。[搜索找到方法](https://blog.hackroad.com/life/1454.html)，记录一下
	
	 修改wp-includes目录下的pluggable.php文件，在最后一行加入如下代码：
	 // 更改默认发信地址
	add_filter('wp_mail_from','mail_from');	function mail_from() {
	$emailaddress = 'admin@yourname.com'; //你的邮箱地址
	return $emailaddress;
	}
	// 更改默认发信人名字
	add_filter('wp_mail_from_name','mail_from_name');
	function mail_from_name() {
	$sendername = 'youname'; //你的名字
	return $sendername;
	}
<!--怎么修改注释都有，网上错误的方法是修改functions.php，我修改过后博客直接打不开了，为什么是修改pluggable.php而不是functions.php？这是pluggable.php中的一段： Using the two 'wp_mail_from' and 'wp_mail_from_name' hooks allow from * creating a from address like 'Name &lt;email@address.com&gt;' when both are set. If * just 'wp_mail_from' is set, then just the email address will be used with no * name. 想必大家都明白了，人家说的很清楚 'wp_mail_from' 和 'wp_mail_from_name' 这两个函数是这里的。-->

