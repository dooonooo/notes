title: 查找附近的点——使用Geohash.class.php
tags:
  - Geohash
  - 附近的点
id: 1607
categories:
  - 电脑网络
date: 2014-09-24 11:08:41
---

在做微信的时候想到很多微信服务号有查找附近门店，网点的功能，如顺丰快递，就可以发送位置信息，就可以得到附近的收寄件网点。

如何实现这样的功能呢？

实现的方法有2种（文章写的比较粗略也，小儿科，高手可以移步至[http://www.wubiao.info/372](http://www.wubiao.info/372 "查找附近的xxx 球面距离以及Geohash方案探讨")）

1.将用户的位置（坐标）与数据库中所有坐标对比，计算出距离，并按距离由远到近进行排序，这方法是不是太笨了

2.高级模式：

因为每个坐标都有两个数，我们平常更关注的长度，两个数就不便于对数排序计算了。
所以我们可以坐标重新编码，编码原理Geohash，参看[维基百科](https://en.wikipedia.org/wiki/Geohash)，或[http://www.wubiao.info/372](http://www.wubiao.info/372 "查找附近的xxx 球面距离以及Geohash方案探讨")，在数据库保存编码。比如：坐标(22.539341，113.995115)按照Geohash编码后为：uxbpbzuxuxyz因为编码规则是将两个坐标的数字交叉进行，所以以后查询附近的点可以用类似LIKE 'uxbpbzux%'语句查询，调整uxbpbzux的长度就可以对附近的距离的值设定了。