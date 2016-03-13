title: Java在windows上开发环境的搭建
tags:
  - java
id: 1540
categories:
  - 电脑网络
date: 2014-07-22 17:52:09
---

1.  下载jdk
下载地址：[http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
选择相对应的版本
[undefined](http://ilidong.com/wp-content/uploads/2014/07/java-1.png)

1.  安装jdk
安装可以直接下一步，下一步……完成安装。可以根据需要更改安装路径。

[undefined](http://ilidong.com/wp-content/uploads/2014/07/java-2.png)

我的安装路径[undefined](http://ilidong.com/wp-content/uploads/2014/07/java-3.png)[undefined](http://ilidong.com/wp-content/uploads/2014/07/java-4.png)

1.  修改环境变量
a． 在“计算机”图标上右击鼠标，选择“属性”命令，在弹出的对话框中，单击左侧的高级系统设置，打开如图的系统属性[undefined](http://ilidong.com/wp-content/uploads/2014/07/java-5.png)

b． 新建 变量名”JAVA_HOME”的变量，变量值为JDK的安装路径

[undefined](http://ilidong.com/wp-content/uploads/2014/07/JAVA_HOME.png)

c． 新建 变量名”CLASSPATH”的变量，变量值为%JAVA_HOME%\lib;%JAVA_HOME%\jre\bin\;（;不可以丢掉）

[undefined](http://ilidong.com/wp-content/uploads/2014/07/PATH.png)

d． 修改path变量：在path变量值最前面添加%JAVA_HOME%\bin;（;不可以丢掉，它是用于分割不同的变量值）[undefined](http://ilidong.com/wp-content/uploads/2014/07/CLASSPATH.png)

1.  验证环境变量是否正确
打开“运行”窗口，输入“cmd”回车；输入java和javac有如图的输出，则Java在 windows开发环境搭建大功告成了

[undefined](http://ilidong.com/wp-content/uploads/2014/07/java-9.png)