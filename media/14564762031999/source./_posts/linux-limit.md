title: linux权限机制
tags:
  - linux
id: 1008
categories:
  - 电脑网络
date: 2013-12-03 23:46:19
---

**权限**
权限是操作系统用来限制对资源访问的机制，权限一般分为读、写、执行。
系统中每一个文件都拥有特定的权限、所属用户及附属组，通过这样的机制来限制哪些用户。哪些组可以对特定的文件进行什么样的操作。
每个进程都是以某个用户的身份运行的，所以进程的权限与该用户的权限一样，用户的权限大，该进程拥有的权限就大。

**文件权限**

Linux中每个文件都拥有以下三种权限：<!--more-->
<table width="100%" border="1" cellspacing="0" cellpadding="2">
<tbody>
<tr>
<td valign="top">权限</td>
<td valign="top">对文件的影响</td>
<td valign="top">对目录的影响</td>
</tr>
<tr>
<td valign="top">r(read读取)</td>
<td valign="top">可读取文件的内容</td>
<td valign="top">可以列出目录内容</td>
</tr>
<tr>
<td valign="top">w(write写入)</td>
<td valign="top">可以修改文件内容</td>
<td valign="top">可在目录中创建删除文件</td>
</tr>
<tr>
<td valign="top">x(执行)</td>
<td valign="top">可以作为命令执行</td>
<td valign="top">可访问目录内容</td>
</tr>
</tbody>
</table>
目录必须拥有x权限，否则无法查看其中的内容

**UGO**
Linux权限基于UGO模型进行控制：

*   U代表User，G代表Group，O代表Other
*   每一个文件的权限基于UGO进行设置
*   权限三个一组（rwx），对应UGO分别设置
*   每一个文件拥有一个所属用户和所属组，对应UG，不属于该文件所属用户或所属组的使用O权限
命令ls -l可以查看当前目录下文件的详细信息

**UGO**

修改文件所属用户、组
命令chown用以改变文件的所属用户：
chown username file
-R 参数递归的修改目录下的所有文件的所属用户
命令chgrp用以改变文件的所属组：
chgrp username file
-R参数递归的修改目录下的所有文件的所属组

**修改权限**
命令chrmod用以修改文件的权限
chmod 模式 文件
-R参数递归的修改目录下的所有文件的权限
模式为如下格式：

*   u、g、o分别代表用户、组、其它
*   a可以代指ugo
*   +、=代表加入或删除对应的权限
*   r、w、x代表三种三种权限
模式示例：
chmod u+rw file
chmod g-x file
chmod go+r file

命令chmod也支持以数字方式修改权限，三个权限分别由三个数字表示：
r = 4
w = 2
x = 1
使用数字表示权限时，每组权限分别为对应数字之和