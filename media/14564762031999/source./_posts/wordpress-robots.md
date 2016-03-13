title: 给wordpress添加robots.txt
tags:
  - wordpress
id: 876
categories:
  - 电脑网络
date: 2013-11-06 19:01:20
---

### Robots.txt的写法

Robots.txt文档以User-agent: 开头，标识语句对应的搜索引擎机器人，后面跟上Disallow: 和Allow：表示起作用的链接。

	User-agent: baiduspider 表示对百度机器人起作用。
	User-agent: * 表示对所有搜索引擎机器人起作用。
	Robots.txt文档中至少要有一条User-agent:记录
	而User-agent: * 记录只允许有一条。
	Disallow: /ilidong 	表示不允许搜索引擎访问或者收录/ilidong.html、/ilidong/index.html、/ilidong.php等包含/ilidong的链接，
	而Disallow: /ilidong/	则允许访问/ilidong.html、/ilidong.php等，但是禁止访问/ilidong/index.html。
	Disallow: / 表示禁止搜索引擎机器人访问收录所有页面。
	Disallow: 	表示允许搜索引擎访问收录所有页面。
	Allow: /ilidong  表示允许搜索引擎访问或者收录/ilidong.html、/ilidong/index.html、/ilidong.php等包含/ilidong的链接，
	Allow:/ilidong/	则表示允许搜索引擎机器人访问/ilidong/index.html等链接，但是对/ilidong.html、/ilidong.php未置可否。

### “*”和“$”通配符

	Disallow: */comments 表示不允许访问和收录所有wordpress评论留言页面。
	比如：http:// ilidong.com/html/1.html#comment-37 是禁止收录的。
	Disallow: /category/*/page/ 表示禁止访问和收录分类的相关分页。
	Disallow: .jpg$ 和Disallow: .php$ 分别表示禁止访问收录“,jpg”和“.php”后缀的文件

我的robots.txt

	User-agent: *
	Disallow: /*?*
	Disallow: /wp-admin
	Disallow: /wp-content/plugins
	Disallow: /wp-content/themes
	Disallow: /wp-includes
	Disallow: /trackback
	Disallow: /feed
	Disallow: /comments
	Disallow: /category/*/page/
	Disallow: /tag/*/page/
	Sitemap: http://ilidong.com/sitemap.html
	Sitemap: http://ilidong.com/sitemap_baidu.xml
