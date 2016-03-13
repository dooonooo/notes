
title: CSS选择器
date: 2016-01-08 22:58:44
categories:
tags:
- css
---
css选择器内容繁多，整理便于理解
<!-- more -->
## 1. 元素选择器

	h1{}
	p{}

### 选择器分组

	h1,p{}
	* 通配符

## 2.类选择器

	.class
	结合元素选择器 a.class
	多类选择器 .class1 .class2{}

## 3.ID选择器

	#id
	

## 4.属性选择器

\[attribute\]:用于选取带有指定属性的元素
	
	//把包含标题的所有元素变成蓝色
	[title]{
		color:blue
	}
[attribute = value]: 选取等于特定属性值的元素，这种格式要求必须与属性值完全匹配

	a[title='w3school']{
		color:red;
	}
\[attribute ~= value\]: 根据部分属性值选择，如果需要根据属性值中的词列表的某个词进行选择（词与词之间用空格分开）则需要使用波浪号（～）

	
\[attribute |= value\]: 选取属性值等于value或以value-开头的所有元素
	
	*[title|='en']{
		color:red;
	}
css3新增属性选择器
	\[att\*=val]包含
	\[att\^=val]开头
	\[att\$=val]结尾

## 5.后代选择器

	p strong{
		color:blue;
	}

## 6.子元素选择器
与后代选择器相比，只能选择作为某元素之元素的元素
	
	h1>strong{
		color:blue;
	}

## 7.相邻兄弟选择器
可选择紧接在另一个元素后的元素(自身没有选择)，且二者有相同的父元素

	h1+p{};

## 8.伪类 
### 结构性伪类选择器（伪元素）（css3）

	/*首行*/
	p:first-line{
		color:bule	
	}
	/*首字母*/
	p:first-letter{
		color:blue
	}
	/*before*/
	li:before{
		content:"---"
	}
	/*after*/
	li:after{
		content:"注释内容"；
		font-size:12px;
	}
	
### root not empty target
在css3中，结构性伪类选择器的特点是允许开发者根据文档中的结构来指定元素的样式。
	
	:root{
		background-color: darkgrey;
		}

	div *:not(h1){
		color:black;
		}
		
	:empty{
	
		}
	:target{
		background-color:orange
		}
		
		
### first-child、last-child、nth-child、nth-last-child
针对一个父元素中的第一个子元素、最后一个子元素、指定序号的子元素
	
		li:first-child{backgroud-color:;}
		li:last-child{}
		li:nth-child(n){}
		li:nth-last-child(n){}
		
		//奇数
		li:nth-child(odd){}
		//偶数	
		li:nth-child(even){}
		
### `:nth-of-type`和`:nth-last-of-type`

`:only-child`
只有一个子元素
可以使用only－child选择器来代替使用nth-child和 nth-last-child的实现方法

### UI元素状态伪类选择器
只有当元素处于某种状态下时才起作用，默认状态下不起作用。

(注意:必须以<span style="color: #ff0000;">L</span>o<span style="color: #ff0000;">v</span>e ,<span style="color: #ff0000;">Ha</span>的顺序来定义锚伪类)

	link、 hover、active、focus、disable、checked
	enabled、disable
	read-only、default、indeterminate、selection、invalid、valid、required、optional、in-range、
	
### 通用兄弟选择器	
同一个父元素之中的某元素之后的所有其他某个种类的兄弟元素所使用样式。


-----
参考：
1. 整理自极客学院视频
2. W3Cschool [CSS 选择器参考手册](http://www.w3school.com.cn/cssref/css_selectors.asp)
3. [CSS选择器](http://www.cnblogs.com/JustYong/p/5015643.html)


