title: 安装repoforge第三方yum源
tags:
  - linux
  - repoforge
id: 1185
categories:
  - 电脑网络
date: 2014-01-06 15:38:28
---

使用linux，时常有些rmp包在centos默认源中没有，需要使用第三方源repoforge。

安装repoforge的方法：

**1.访问repoforge网站：**

<http://repoforge.org/use/>

**2.下载对应版本**
使用centos 64bit的下载链接为：
{% blockquote %}
wget http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el6.rf.x86_64.rpm
{% endblockquote %}

**3．安装 rpm包**

```rpm –ivh rpmforge-release-0.5.3-1.el6.rf.x86_64.rpm```

**4.更新源信息：**
{% blockquote %}
yum clean all	
yum list  
{% endblockquote %}