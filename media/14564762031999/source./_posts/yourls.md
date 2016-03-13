title: Yourls 开启自己的短网址
tags:
  - 开源
  - 短网址
id: 1333
categories:
  - 电脑网络
date: 2014-04-05 23:41:54
---

在wordpress中有一个插件，也是可以实现短网址的功能，但是太依赖wordpress了，不能将链接定义到目录（也许是我笨，不会弄）。

[undefined](http://ilidong.com/wp-content/uploads/2014/04/yourls.png)

现在发现了yourls这个开源项目，可以独立运行。同样有统计，书签等功能。并且更加强大。

现在就说说怎么弄吧

下载Yourls  https://codeload.github.com/YOURLS/YOURLS/zip/master

Yourls的安装比较简单。

**1.****修改配置文件：user\config-sample.php**

[php]

	define( 'YOURLS_DB_USER', 'your db user name' );// MySQL 数据库用户名
	
	define( 'YOURLS_DB_PASS', 'your db password' );// MySQL 数据库密码
	
	define( 'YOURLS_DB_NAME', 'yourls' );// MySQL 数据库名称
	
	define( 'YOURLS_DB_HOST', 'localhost' );// MySQL 数据库所在主机。
	
	define( 'YOURLS_DB_PREFIX', 'yourls_' );/**创建的 Yourls 的表的名字前缀，同一个数据库放多个 Yourls 程序时需要修改。*/
	
	define( 'YOURLS_SITE', 'http://site.com' );//站点域名
	
	define( 'YOURLS_HOURS_OFFSET', 0 ); //时区修改，基本没必要
	
	define( 'YOURLS_LANG', '' ); //设置语言
	
	define( 'YOURLS_UNIQUE_URLS', true );//只允许一个要被缩短网址对应一个短网址，若允许对应多个短网址写false
	
	define( 'YOURLS_PRIVATE', true );//私人用还是公开用，公开的话写false
	
	define( 'YOURLS_COOKIEKEY', 'modify this text with something random' );//访问 http://yourls.org/cookiekey.php  取得一个唯一的 Key 并且修改填入
	
	$yourls_user_passwords = array(
		'username' =&gt; 'password',
		'username2' =&gt; 'password2'	// You can have one or more 'login'=&gt;'password' lines
		);/**username管理员用户名和password密码，默认两组，可删除一组或增加N组 */
	
	define( 'YOURLS_DEBUG', false );//是否开启调试模式
	
	define( 'YOURLS_URL_CONVERT', 36 );//设置url编码
	
	$yourls_reserved_URL = array(
		'porn', 'faggot', 'sex', 'nigger', 'fuck', 'cunt', 'dick', 'gay',
	);/** 保留词语，建议增加proxy等词。*/
	


关于url编码：

Yourls 提供两种 URL 编码形式，一种是只有小写的 Base 36 

	encoding：
	0123456789abcdefghijklmnopqrstuvwxyz，
	
还有一种是有大小写的 Base 62 encoding：

	123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz，

一般来说，使用默认的 Base 36 即可，因为要使用 Base 62 需要空间支持 php 的 BCMath 扩展，个人用 Base 32 足矣，官方宣称可以创建4,738,381,338,321,617,846 个短网址，所以没什么特殊情况就不用修改 config.php ，用默认的编码即可。
然后把 config-sample.php 重命名为 config.php ，确保你的空间支持 PHP + MySQL 以及基本的几个组件（Mod-Rewrite功能，Curl 等，一般的空间都支持）

**2.安装**

将文件上传你的网站某个目录
执行 http://你的地址/目录名/admin/install.php 进行安装即可。
比如我是上传到go目录，执行 http://ilidong/go/admin/install.php 进行安装。