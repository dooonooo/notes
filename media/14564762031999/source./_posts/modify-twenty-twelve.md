title: 修改我的Twenty Twelve主题——添加本文链接
tags:
  - wordpress
  - 主题
id: 1093
categories:
  - 电脑网络
date: 2013-12-29 23:46:55
---

Twenty Twelve主题是现在wordpress自带的最旧的主题，这个主题个人觉得很清爽、简单。也是一个响应式设计的主题。加上俺对自己设计主题冇信心。所以选择了这个主题。但是这个主题还是有些不符合我们的习惯。

**1.添加本文链接**
为了不让别人盗取自己的劳动成果,在文章末尾添加本文的链接地址,来防止别人采集我们的文章。
方法：
修改主题目录里的content.php文件

在<!– .entry-content –>之前添加

	<div> 转载请注明来源：<a href=“<?php bloginfo(‘url’); ?>”><?php bloginfo(‘name’); ?></a>-<a href=“<?php the_permalink() ?>”> <?php the_title(); ?></a> </div> <div> 本文链接地址：<a href=“<?php the_permalink() ?>”><?php the_permalink() ?></a> 
	</div> 

**2.修改feed地址**
昨天设置了[二级域名发布RSS Feed](http://ilidong.com/html/1087.html "在WordPress中使用二级域名发布RSS Feed")，但是有些阅读器可以通过输入网址自动识别feed地址，比如feedly，reeder都可以通过输入ilidong.com自动找到本站的feed地址，但是它自动识别的是http://ilidong.com/feed,原理是通过抓取首页的源代码 &lt;link rel="alternate" type="application/rss+xml" title="" /&gt;来识别，原来为

	<link title=“iLiDong » Feed” href=“http://www.ilidong.com/feed” rel=“alternate” type=“application/rss+xml” />
通过在主题的funtion.php文件中添加

	function custom_rss($output, $show) { if (in_array($show, array(‘rss_url’, ‘rss2_url’, ‘rss’, ‘rss2’, “))) $output = ‘your_custom_rss_feed_url_goes_here’; return $output; } add_filter(‘bloginfo_url’, ‘custom_rss’, 10, 2); add_filter(‘feed_link’, ‘custom_rss’, 10, 2); 

现在源码中已经是

	<link title=“iLiDong » Feed” href=“http://feed.ilidong.com” rel=“alternate” type=“application/rss+xml” />

阅读器可以自动识别feed地址是http://feed.ilidong.com