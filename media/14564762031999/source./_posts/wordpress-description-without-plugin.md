title: wordpress不用任何插件，添加描述
tags:
  - SEO
  - wordpress
id: 477
categories:
  - 电脑网络
date: 2012-12-28 20:33:42
---

今天突然想给网站添加加一个描述（description），用插件确实可以，但是只想添加一个描述，就动用插件也未免太大动干戈了吧?!然后咧，我找到了一个方法：

添加几行代码就可以了。
	
	<?php if (is_home()) { ?>  //判断是不是首页
	<meta name=“keywords” content=“”/>  //加上你的关键字
	<meta name=”description” content=“”/> //加上你的描述
	<?php } ?>
	
将这几行代码放在header文件之前,或者放在之后即可，
就这么简单就这么几行代码即可搞定。