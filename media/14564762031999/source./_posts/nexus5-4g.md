title: Nexus5使用中国移动4G网络
tags:
  - 4G
  - Nexus5
id: 1316
categories:
  - 电脑网络
date: 2014-04-02 20:45:39
---

[undefined](http://ilidong.com/wp-content/uploads/2014/04/cb00e82e22bff7e1c9a0b0393559b14e.jpg)只因为Nexus5是Google出品，购买之后才发现它居然也支持中国移动4G LTE-TDD网络，（只有B820版本支持，即北美版）当然我的就是美版，当时只是因为美版便宜就买了美版的Nexus5，没想到就提前成了中国移动4G用户。据说这个版本也支持电信的网络，但我没有折腾，所以不作评价。

开通4G功能的方法，网上已经很多，我就不copy了。这有一个来自机锋论坛的教程：
[美版Nexus5开启移动4G教程.pdf](http://ilidong.com/wp-content/uploads/2014/04/美版Nexus5开启移动4G教程（详细版）.pdf)

这里提供相关软件下载：
[platform-tools](http://ilidong.com/wp-content/uploads/2014/04/platform-tools.zip)
[Field Test Mode_com](http://ilidong.com/wp-content/uploads/2014/04/Field-Test-Mode_com.zip)

Nexus5毕竟不是国货，要使用中国移动的4G是不会那么一帆风顺的，Nexus5只支持中国移动4G的频段只有一个频段，band41，但是这个频段只有新建的4G基站支持，中国移动宣传的4G覆盖，很多都是band38，这是13年底的新闻 [黄宇红：2014年中国移动将加快Band41的全面支持](http://www.cctime.com/html/2013-11-15/201311151035108377.htm)，所以相信很快nexus5可以在很多地方连上4G信号。在武汉的城区有些地方已经覆盖了。（我所在的地方太偏了，还木有信号，还是只能使用苦逼E网。）

还有一些问题：
Nexus5开启band41 4G网络后，它不会去自动去搜索4G网络，需要手动设置。在拨号界面输入*#*#4636#*#*，选择第一项 手机信息，在设置首选网络类型中选择LTE only，Nexus5才会去搜索LTE网络，（如果两三分钟都没有信号，那就说明你所在的地方没有band41信号。）当连接到LTE，再选择LTE/GSM auto。当有电话打进来是Nexus5就会自动切换成2G网络。（注：中国移动技术还不成熟，4G还打不了电话）

结语：我只想说Nexus5要使用4G还真不容易。也只能怪Google和Government关系不好