title: 删除wordpress的google font字体
tags:
  - google font
  - wordprees
id: 1404
categories:
  - 电脑网络
date: 2014-04-16 23:50:37
---

删除wordpress的google font字体
网站搬家后，测试的时候发现清除缓存后，博客载入都很慢，使用百度站长工具发现其中的font.google.com需要20多秒
一看到google你懂得，于是我想移除，感觉在header.php中
但是在header.php怎么也找不到。于是用google去找google的问题，原来早有先例
我用了比较简单的方法在主题的function.php 添加
{% blockquote %}
class Disable_Google_Fonts {
 public function __construct() {
 add_filter( 'gettext_with_context', array( $this, 'disable_open_sans'), 888, 4 );
 }
 public function disable_open_sans( $translations, $text, $context, $domain ) {
 if ( 'Open Sans font: on or off' == $context &amp;&amp; 'on' == $text ) {
 $translations = 'off';
 }
 return $translations;
 }
 }
 $disable_google_fonts = new Disable_Google_Fonts;
{% endblockquote %}
如果你真要找到这个字体在wordpress的位置，那我也告诉你，它在在/wp-includes/script-loader.php中
大约在581行，把//fonts.googleapis.com/...这行代码删除即可。
又或者貌似有个插件叫Disable Google Fonts，直接安装这个插件也行。