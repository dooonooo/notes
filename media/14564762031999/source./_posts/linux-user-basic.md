title: linux用户基础
tags:
  - linux
id: 1006
categories:
  - 电脑网络
date: 2013-12-03 23:44:58
---

**用户、组**
当我们使用Linux时，需要以一个用户的身份登入，一个进程也需要以一个用户的身份运行，用户限制使用者或进程可以使用、不可以使用哪些资源。

**组用来方便组织管理用户**

*   每一个用户拥有一个UserID，操作系统实际使用的是用户ID，而非用户名
*   每一个用户属于一个主组，属于宇哥或多个附属组
*   每一个组都拥有一个GroupID
*   每一个进程以一个用户身份运行，并受该用户可访问的资源限制
*   每个可登录用户拥有一个指定的shell（界面）
**<!--more-->用户**
用户ID为32位，从0开始，但是为了和老式系统兼容，用户ID限制在60000以下。
用户的分类
分为以下三种：

*   root用户（ID为0的用户为root）
*   系统用户（1-499）
*   普通用户（500以上）
系统中的文件都有一个所属用户及所属组
使用id命令可以显示当前用户的信息
使用passwd命令修改当前用户密码

相关文件
/etc/passwd 保存用户信息
/etc/shadow 保存用户密码（加密的）
/etc/group 保存组信息

查看登陆的用户
命令whoami显示当前用户
命令who显示有哪些用户已经登录系统
命令w显示有哪些用户已经登陆并且在干什么

**创建一个用户**
命令useradd用以创建一个新用户
useradd username
这个命令会执行以下操作
1.在/etc/passwd中添加用户信息
2.如果使用passwd命令创建密码，则将密码加密保存在/ect/shadow
3.为用户建立一个新的家目录/home/username
4.将/etc/skel中的文件复制到用户的家目录中
5.建立一个与用户用户名相同的组，新建用户默认属于这个同名组
命令useradd支持以下参数：
-d家目录
-s登录shell
-uuserid
-g主组
-G 附属组（最多31个，用“，分割”）
也可以通过直接修改/etc/passwd的方式实现（不建议）

**修改用户信息**
命令usermod用来修改用户信息
usermod 参数 username
命令usermod 支持以下参数：
-l 新用户
-u 新userid
-d 用户家目录位置
-g 用户所属主组
-G 用户所属附属组
-L 锁定用户使其不能登录
-U 解除锁定

**删除用户**
命令userdel用以删除用户
userdel username （保存用户的home目录）
userdel -r username（删除用户的ome目录）

**组**
几乎所有的操作系统都有组的概念，通过组，我们可以更加方便的归类、管理用户。一般来讲，我们使用部门、职能或地理区域的分类方式来创建使用组。

*   每个组有一个组ID
*   组信息保存在/etc/group
*   每个用户拥有一个主组，同时还可以拥有最多31个附属组
**创建、修改、删除组**
命令groupadd用以创建组：
groupadd ilidong
命令groupmod用以修改组信息：
groupmod -n newname oldname 修改组名
groupmod -g newGID oldGID 修改组ID
命令groupdel用以删除组：
groupdel ilidong