title: 《JavaScript权威指南》读书笔记1
date: 2016-01-02 23:22:20
categories:
tags:
- JavaScript
- 读书笔记
---

学了好久WEB，只因为没有认真学习JavaScript，做不出完整效果来，现在要认真看书记笔记了
<!-- more -->
![JavaScript权威指南](/media/s8958854.jpg)

## 词法结构
当函数赋值给对象的属性，我们称为“方法”

按照惯例，构造函数均以大写字母开始

JavaScript是区分大小写的语言

JavaScript会忽略程序中标示之间的空格。多数情况下，JavaScript同样会忽略换行符（可选分号情形）

JavaScript支持两种格式的注释：
	
	//单行注释 
	
	/*
	多行注释内容
	*/
	
	
（1）javascript保留字

- if分支语句：if, else
- switch分支语句：switch, case, default, break
- 循环语句：do, while, for, continue
- 异常处理语句：try, catch, finally, throw
- 获取类型：typeof, instanceof
- 布尔值：true, false, null
- 函数相关：var, void, function, return
- 其他：in, this, with, new, delete

（2）ECMA扩展保留的关键字

- 基本数据类型：byte, char, boolean, int, short, long, float, double, enum
- 继承：implements, extends, super
- 类与接口：class, interface
- 用来修饰函数的关键字：abstract, native, static, final, const, volatile, synchronized
- 导入导出：export, import
- 访问权限：private, protected, public
- 其他：goto, package, throws, transient, debugger

（3）javascript预定义的全局变量名或函数名

- 数据类型：Number, Boolean, String, undefined, Object, Array, Function, Date, Math, RegExp, Error
- 错误类型：EvalError, RangeError, ReferenceError, SyntaxError, TypeError, URIError
- 编码：decodeURI, decodeURIComponent, encodeURI
- 转义：escape, unescape
- 类型转换：parentInt, parentFloat
- 特殊值及判断：isFinite, isNaN, NaN, Infinity
- 其他：arguments, eval


## 类型、值和变量

在JavaScript中，字符串是不可变的，可以访问字符串任意位置的文本，但JavaScript并没有提供修改已知字符串的文本内容的方法。


### 数字

JavaScript中算术运算在溢出、下溢、被零整除时不会报错。
零除以零是没有意义的


数字中的特殊值：

- Infinity：表示无穷大的特殊值
- NaN：特殊的非数字值（产生未定义的结果或错误时出现，如除0）
- Number.MAX_VALUE：可表示的最大数字
- Number.MIN_VALUE：可表示的最小数字（与0最接近的数字）
- Number.NaN：特殊的非数字值
- Number.POSITIVE_INFINITY：表示正无穷大的特殊值
- Number.NEGATIVE_INFINITY：表示负无穷大的特殊值

注意：NaN和任何数值都不相等，包括它自己在内，因此需要用isNaN()来检测。isFinite()用来检测一个数字是否是NaN、正无穷大或负无穷大。

### 文本
由单引号定界的字符串中可以包含双引号，由双引号定界的字符串中也可以包含单引号。

字符串可调用的方法

	var s ="Hello,World"  //定义一个字符串
	s.length  // => "11"  
	s.chaAt(0)  // => "H": 第一个字符
	s.charAt(s.length-1)  //  => "d" :最后一个字符
	s.substring(1,4)  //  => "ell" :第2-4个字符
	s.slice(1,4)  //  => "ell" :同上
	s.slice(-3)  //  => "rld" :最后三个字符
	s.indexOf("l")  //  => "2" :字符l首次出现的位置
	s.lastIndexOf("l")  //  => "10" : 字符l最后一次出现的位置
	s.indexOf("l",3)  //  => 3 :在位置3及以后首次出现l的位置
	s.split(",")  //  => ["Hello","World"] : 分割成字串
	s.replace("H","h")  //  => "hello,World" :全文字符替换
	s.toUpperCase()  //  => "HELLO,WORLD" :大写


