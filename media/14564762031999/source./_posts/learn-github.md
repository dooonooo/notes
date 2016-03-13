title: github入门
tags:
  - git
id: 1570
categories:
  - 电脑网络
date: 2014-09-09 11:25:32
---

1.下载msysgit，[http://msysgit.github.io/](http://msysgit.github.io/ "下载msysgit")，按照默认设置安装即可
安装完成后，在开始菜单里找到“Git”-&gt;“Git Bash”，出现一个类似命令行窗口的东西，就说明Git安装成功！

2.添加全局设置,设置你的名字和Email地址

{% blockquote %}
$ git config --global user.name &quot;Your Name&quot;
$ git config --global user.email &quot;email@example.com&quot;{% endblockquote %}

3.创建版本库

{% blockquote %}
$ mkdir test
$ cd test
$ git init
$ git add readme.txt
$ git commit -m &quot;wrote a readme file&quot;
{% endblockquote %}