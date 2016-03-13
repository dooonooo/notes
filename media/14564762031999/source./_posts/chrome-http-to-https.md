title: chrome下强制将http重定向到https
tags:
  - chrome
  - https
id: 1486
categories:
  - 生活感悟
date: 2014-06-05 11:09:32
---

起因：因为使用https有很多奇葩的问题不能于是取消了[强制使用https](http://ilidong.com/html/1359.html "保护数据安全，开启全站HTTPS")，而是https和http同时使用，但是有时候https，有时候http，把wprdpress都搞晕了，我就像能不能使用浏览器来重定向https。

虽然有https everywhere这种强大的扩展程序，但貌似不能自定义规则，或是很复杂（博主太笨了）。最近发现，原来chrome自身就可以设置重定向到https。

打开chrome，在地址栏输入chrome://net-internals/#hsts

在Domain中填写需要重定向的网站域名（红色框中）比如：ilidong.com

然后点击add。
[undefined](http://static.ilidong.com/images/chrome-https.png)
以后访问ilidong.com都会重定向到https://ilidong.com了

**UPDATE:**因为本站最近使用了安全宝，所以https失效了。需要如需体验小站的https可以修改hosts，指向本站源ip:114.215.180.22,就可以https访问了。