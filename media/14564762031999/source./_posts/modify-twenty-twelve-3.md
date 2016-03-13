title: 修改我的Twenty Twelve主题（3）——首页自动摘要输出及长度修改
tags:
  - wordpress
  - 主题
id: 1144
categories:
  - 电脑网络
date: 2014-01-03 17:07:45
---

要首页实现摘要输出可以使用<!–more–>，但是不够美观，有时忘记了添加<!—more–>，就在全文输出了,影响美观。

**1.首页摘要输出**

其实Twenty Twelve主题本身是有摘要输出的影子的，当使用搜索是搜索结果就是摘要输出的。在主题的content.php文件中你会发现这样的代码：

	<?php if ( is_search()) : // Only display Excerpts for Search ?>

	<?php the_excerpt(); ?>

没错the_excerpt();就是wordpress中的摘要输出函数。

在is_search()后，以||隔开，

添加is_home()，首页就是摘要输出

添加is_category()，分类页摘要输出

添加is_archive()，存档页摘要输出

一般我们需要在内容页全文输出，在首页、搜索结果页，分类页、存档页都是摘要输出，所以我们可以将

	<?php if ( is_search()) : // Only display Excerpts for Search ?>

改成

	<?php if (is_home()||is_search()||is_category()||is_archive()):?>

如果你是英文网站，那就可以到此结束了。

**2.修改摘要长度**

但是如果是中文网站，你会发现首页输出的内容太少了。接下来就是修改摘要长度。

在网上搜索，很多人说在主题的functions.php中添加自定义函数。

	function chinese_excerpt($text, $lenth=100) { $text = mb_substr($text,0, $lenth); return $ text; } add_filter(‘the_excerpt’, chinese_excerpt');


这样有好处，当以后升级wordpress版本的时候，只要不升级主题，不作修改，首页照样能自动摘要输出。

但是不知道是我的水平问题，还是主题、主机问题，反正就是不能实现。于是从wordpress文件着手，修改wp-includes目录下的formatting.php（不是functions.php）文件。

将

	[excerpt_length = apply_filters( ‘excerpt_length’, 55 );

修改为

	$excerpt_length = apply_filters( ‘excerpt_length’, 200 );
代码大约在2373行。

当然这种方法会在升级wordpress被覆盖，也就是说在每次升级后要修改一下。