title: linux下获取帮助
tags:
  - linux
  - 帮助
id: 1002
categories:
  - 电脑网络
date: 2013-12-02 23:47:32
---

**没有必要记住所有的东西**

help
几乎所有命令都可以使用-h或--help参数获取使用方法、参数信息

**man**
man命令
man文档分为很多类型：
man 数字 查看的命令 用来查看相关文档

<!--more-->
<table width="60%" border="1" cellspacing="0" cellpadding="2">
<tbody>
<tr>
<td valign="top">部分</td>
<td valign="top">类型</td>
</tr>
<tr>
<td valign="top">1</td>
<td valign="top">用户命令</td>
</tr>
<tr>
<td valign="top">2</td>
<td valign="top">内核系统调用</td>
</tr>
<tr>
<td valign="top">3</td>
<td valign="top">库函数</td>
</tr>
<tr>
<td valign="top">4</td>
<td valign="top">特殊文件和设备</td>
</tr>
<tr>
<td valign="top">5</td>
<td valign="top">文件格式和规范（常用）</td>
</tr>
<tr>
<td valign="top">6</td>
<td valign="top">游戏</td>
</tr>
<tr>
<td valign="top">7</td>
<td valign="top">规范、标准和其他页面</td>
</tr>
<tr>
<td valign="top">8</td>
<td valign="top">系统管理命令</td>
</tr>
<tr>
<td valign="top">9</td>
<td valign="top">Linux内核API</td>
</tr>
</tbody>
</table>
man -k 关键字  用来查询包含该关键字的文档

**info**

info与man类似，但是提供的信息更加详细，以类似网页的形式显示

man与info都可以通过“/+关键字”方式进行搜索

**DOC**
很多程序、命令都带有详细的文档，以TXT、HYML、PDF等方式保存在/usr/share/doc目录下，这些文档是相关程序最为详尽的文档。

最最终极方法：上网google一下。