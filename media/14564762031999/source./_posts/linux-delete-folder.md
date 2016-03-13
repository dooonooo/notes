title: linux下如何删除文件夹
tags:
  - linux
id: 91
categories:
  - 电脑网络
date: 2013-11-05 04:10:53
---

rm -rf 目录名字
-r 就是向下递归，不管有多少级目录，一并删除
-f 就是直接强行删除，不作任何提示的意思

删除文件夹实例：
rm -rf /var/log/httpd/access
将会删除/var/log/httpd/access目录以及其下所有文件、文件夹
(这里曾出现个问题,如果直接如此使用的话系统可能不会授权这个操作,并出来 Permission denied 的提示
这事你需要在 rm -rf 前补充 sudo 作为授权操作的许可, 即:
sudo rm -rf 文件夹的名字)

需要提醒的是：使用这个rm -rf的时候一定要格外小心，linux没有回收站的

当然，rm还有更多的其他参数和用法，man rm就可以查看了

删除文件使用实例：
rm -f /var/log/httpd/access.log
将会强制删除/var/log/httpd/access.log这个文件

还有一种方法也挺好用:
mkdir 可以创建目录~~~rmdir是删除目录！~~~~