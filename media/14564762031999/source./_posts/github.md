title: github仓库使用
tags:
  - git
id: 1574
categories:
  - 
date: 2014-09-09 14:09:26
---

### 1.生成SSH keys

email修改成你自己的email地址

然后就可以一路回车，使用默认值即可
	
	$ ssh-keygen -t rsa -C "youremail@example.com"
	
看到如下画面就说明SSH keys已经生成

[undefined](http://ilidong.com/wp-content/uploads/2014/09/20140909114443.png)


### 2.将生成的SSH keys添加到github

登陆GitHub，打开“settings”，“SSH Keys”页面，

将id_rsa.pub文件用文本编辑器打开，把其中的内容全部粘贴到key里面。

测试链接

	$ ssh -T git@github.com

提示是否继续连接，yes后，你将看到如下信息，说明你已经

    Hi "username"! You've successfully authentiated,but GitHub does not provide shell access.

### 3.将本地库与github仓库同步

在github创建一个仓库
[undefined](http://ilidong.com/wp-content/uploads/2014/09/20140909134018.png)
执行下面命令(执行其中一步即可)
{% codeblock %}创建一个新的仓库
$ mkdir test
$ cd test
$ git init
$ touch README
$ git add README
$ git commit -m 'first commit'
$ git remote add origin git@github.com:ilidong/test.git
$ git push -u origin master(第一次推送需要加-u参数，之后的推送不需要加-u参数)

推送（push）一个已有的仓库(如仓库已经创建了)
$ git remote add origin git@github.com:ilidong/test.git
$ git push -u origin master(第一次推送需要加-u参数，之后的推送不需要加-u参数)
{% endcodeblock %}

### 4.从github仓库将内容克隆到本地

	$ git clone git@github.com:ilidong/test.git