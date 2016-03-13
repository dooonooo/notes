title: 修改我的Twenty Twelve主题（2）——添加分页导航
tags:
  - wordpress
  - 主题
id: 1101
categories:
  - 电脑网络
date: 2013-12-30 13:05:04
---

Twenty Twelve默认没有分页导航，默认的导航是：早期的文章和较新的文章undefined

修改模板函数(functions.php)
在最后面添加

	/* pagenavi */ function pagenavi( $before = “, $after = ”, $p = 2 ) { if ( is_singular() ) return; global $wp_query, $paged; $max_page = $wp_query->max_num_pages; if ( $max_page == 1 ) return; if ( empty( $paged ) ) $paged = 1; echo $before.‘<div id=“pagenavi”>’.“\n”; echo ‘<span class=“pages”>Page: ’ . $paged . ‘ of ’ . $max_page . ‘ </span>’; if ( $paged > 1 ) p_link( $paged - 1, ‘Previous Page’, ‘上一页’ ); if ( $paged > $p + 1 ) p_link( 1, ‘First Page’ ); if ( $paged > $p + 2 ) echo ‘… ’; for( $i = $paged - $p; $i <= $paged + $p; $i++ ) { if ( $i > 0 && $i <= $max_page ) $i == $paged ? print “<span class=‘page-numbers current’>{$i}</span>” : p_link( $i ); } if ( $paged < $max_page - $p - 1 ) echo ‘… ’; if ( $paged < $max_page - $p ) p_link( $max_page, ‘Last Page’ ); if ( $paged < $max_page ) p_link( $paged + 1,‘Next Page’, ‘下一页’ ); echo ‘</div>’.$after.“\n”; } function p_link( $i, $title = “, $linktype = ” ) { if ( $title == “ ) $title = "Page {$i}”; if ( $linktype == “ ) { $linktext = $i; } else { $linktext = $linktype; } echo ”<a class=‘page-numbers’ href=‘“, esc_html( get_pagenum_link( $i ) ), ”’ title=‘{$title}’>{$linktext}</a>“; }

修改首页模板(index.php)

找到代码

	<?php twentytwelve_content_nav( ‘nav-below’ );?>

修改为

	<?php twentytwelve_content_nav( ‘nav-below’ ); pagenavi();?>

修改样式表(style.css)
在最后加入下面代码

	/* pagenavi */
	#pagenavi a, #pagenavi a:visited, #pagenavi span {
	height: 25px;
	line-height: 25px;
	display: inline-block;
	padding: 1px 8px;
	}
	#pagenavi a, #pagenavi a:visited {
	margin: 0 2px;
	}
	#pagenavi span.pages {
	color: #777;
	font-weight: bold;
	margin-right: 10px;
	padding: 0;
	}
	#pagenavi span.current {
	margin: -2px 2px -1px;
	padding: 0 9px;
	height: 28px;
	line-height: 28px;
	text-align: center;
	}

修改后的导航就成
undefined

参考:不太小的博客 http://butaixiao.com/2013/05/wordpress_pagenav/