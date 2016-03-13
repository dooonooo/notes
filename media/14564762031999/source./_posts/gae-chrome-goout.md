title: GAE+chrome 翻墙教程
tags:
  - goagent
  - 翻墙
id: 612
categories:
  - 电脑网络
date: 2013-05-26 23:50:14
---

生活在神奇的国度，被GFW保护着，但我们已经长大，为了挣脱束缚，于是我们就学会了翻墙。
也许你不需要，但也许某一天你想看看 油土鳖、非死不可、推特儿，所以还是学会翻墙以备不时之用。
本文介绍的是用google app engine (gae)翻墙。(Google虽然退出中国了，但是Google没有离开我们)。
毕竟google是大牌，安全性肯定比那些无名小辈要强得多。
———————————————废话说到此——————————————————
——————————————下面正式开始——————————————————
准备工作：
1.chrome浏览器（没有可以到[http://chrome.google.com](http://chrome.google.com)下载，或者找百度吧）
2.一个google帐号
3.[goagent主程序](http://ilidong.com/wp-content/uploads/2013/05/goagent.zip)
操作步骤：
1.进入[https://appengine.google.com/](https://appengine.google.com/)，用google帐号登录。[undefined](http://ilidong.com/wp-content/uploads/2013/05/login-google.png)

2.然后点击Create Application进入下一步。

[undefined](http://ilidong.com/wp-content/uploads/2013/05/Create-Application.png)

3.填写手机号码

[undefined](http://ilidong.com/wp-content/uploads/2013/05/input-phone-number.png)

4.填写验证码

[undefined](http://ilidong.com/wp-content/uploads/2013/05/input-code.png)

5.按图填写相关信息，appid要记住，稍后要使用

[undefined](http://ilidong.com/wp-content/uploads/2013/05/input-data.png)
6.点击Create Application，即完成了注册。
[undefined](http://ilidong.com/wp-content/uploads/2013/05/success.png)
7.下载[goagent程序](http://ilidong.com/wp-content/uploads/2013/05/goagent.zip)，解压得到两个文件夹

[undefined](http://ilidong.com/wp-content/uploads/2013/05/folder.png)

8.修改 localproxy.ini 中[gae] 下的appid=&lt;你申请到的appid&gt;，多个appid用|分开 ，并将profile=google_cn改成google_hk，否则无法打开Google。

[undefined](http://ilidong.com/wp-content/uploads/2013/05/change-proxy.png)

9.双击serveruploader.bat, 输入你的appid和Gmail帐号，密码，(linux/mac用户请运行uploader.py)上传到服务端，多个appid用|隔开，上传成功后无需再设置proxy.ini文件，请无视黑框里最后的提示。

[undefined](http://ilidong.com/wp-content/uploads/2013/05/upserver.png)[undefined](http://ilidong.com/wp-content/uploads/2013/05/input-mail-and-pw.png)

[undefined](http://ilidong.com/wp-content/uploads/2013/05/upsucess.png)
10.打开chrome浏览器 ，安装Proxy SwitchySharp扩展程序（[https://chrome.google.com/webstore/detail/proxy-switchysharp/dpplabbmogkhghncfbfdeeokoefdjegm](https://chrome.google.com/webstore/detail/proxy-switchysharp/dpplabbmogkhghncfbfdeeokoefdjegm)）

[undefined](http://ilidong.com/wp-content/uploads/2013/05/proxy-switchysharp.png)

11.之后浏览器就会自动弹出Switchy Sharp的配置界面，点击【导入/到导出栏】，点击从文件恢复。（[配置文件下载](http://ilidong.com/wp-content/uploads/2013/05/SwitchyOptions.zip)）

[undefined](http://ilidong.com/wp-content/uploads/2013/05/SwitchySharp1.png) [undefined](http://ilidong.com/wp-content/uploads/2013/05/SwitchySharp.png)
12.最后点击右上角的小地球图标，选择你需要的代理方式，推荐使用自动切换模式。
注意：每次使用时需要把GoAgent开启噢。（或加入开机启动项）

现在你就可以尽情使用 油土鳖、非死不可、推特儿。