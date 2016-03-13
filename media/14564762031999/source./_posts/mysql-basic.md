title: MYSQL 命令行基本操作
date: 2016-01-01 22:10:00
categories:
tags:
- 基本操作
- mysql
---
mysql命令行的基本操作命令
 <!--more-->
## 登录

	mysql -u root -p/mysql-h localhost -u root -p databasrName;

## 数据库操作	

	显示所有数据库
	show databases；
		
	选定某个数据库
	use 数据库名;
	
	创建数据库
	create database 数据库名;
	
	删除数据库
	drop database 数据库名;
	
	查询数据库版本
	select version;
	
	查询当前选定的数据库
	select database();

## 表操作

	创建表
	create table 表名；
	
	删除表
	drop table 表名;
	
	清空表
	delete table 表名;
	
	查看表内容
	select * from 表名;
	
	查看表结构
	describe 表名;
	
	修改表内容
	update表名set 参数名要改成的值where参数名＝某个值;



## 用户操作

	创建用户
	grant 权限 on 数据库名.* to 用户名@登录主机 identified by "密码";
	
	用户已存在赋予权限
	grant select, indert,update,delete on 数据库.* to 用户名@登录主机 identified by "密码"；
	
	权限有14种
	select,insert,update,create,drop,index,altergrant,references,reload,shutdown,process
	
	删除用户
	drop user 用户名;
	
	查询所有用户
	select user from mysql.user
	
	查看当前用户
	select user();
	
## 其它

	查看存储过程
	show procedure status;
	
	查看存储的具体内容
	show create procedure 存储过程名;
	查询时间
	select now();


参考：
http://www.cnblogs.com/JAYIT/p/5016688.html
http://blog.csdn.net/wangbofei/article/details/11357181



