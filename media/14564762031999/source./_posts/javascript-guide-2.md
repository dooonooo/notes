title: 《JavaScript权威指南》读书笔记2－对象
date: 2016-01-12 23:52:25
categories:
tags:
- javascript
- 读书笔记
---
JavaScript对象
<!--more-->
## 对象创建
### 对象直接量
对象直接量是由若干名/值对组成的映射表，名/值对中间用分号分割，名/值对之间用逗号分隔

	var empty = {};  //没有任何属性的对象
	var point = {x:0, y:0}  //两个属性
	var point2 = {x:point.x, y:point.y+1}  //更复杂的值
	var book = {
		"main title": "javascript",  //属性名中有空格，必须用字符串表示
		'sub-title': "the definitive guide",  //属性名中有连字符，必须用字符串表示
		'for': "all audiences",  //"for " 是保留字，因此必须用引号
		author: {  //这个属性值是一个对象
			firstname: "David"
			surname: "flanagan"
		}
	};

### 通过new创建对象

	var o = new Object(); //创建一个空对象，和{}一样
	var a = new Array(); // 创建一个空数组，和[]一样
	var d = new Date();  //创建一个表示当前时间的data对象
	var r = new RegExp();  //创建一个可以进行模式匹配的RegExp对象

### Object.create()
第一个参数是这个对象的原型，第二个可选参数用于对对象的属性进行进一步描述。

## 属性的查询和设置
可以通过点`.`或方括号`[]`运算符来获取属性的值，对于点`.`来说，右侧必须是一个以属性名称命名的简单标识符，对于方括号来说`[]`，方括号内必须是一个计算结果为字符串的表达式，这个字符串就是属性的名字
	
	var author ＝ book.author; //得到book的 "author" 属性

## 删除属性

	delete book.author; //book不再有属性author

delete只是断开属性和宿主对象的联系，不会操作属性中的属性。
只能删除自有属性不能删除继承属性

## 检测属性
in运算符、hasOwnPreperty()、propertyIsEnumerable()

	检测对象的含有自有属性或继承属性，返回true
	var o = {x:1}
	"x" in o;  //true "x"是o的属性
	"y" in o;  //false "y"不是o的属性
	"toString" in o; //true o继承toString属性
	
`hasOwnPreperty()` 自有属性ture，继承属性false
`propertyIsEnumerable()` 只有检测自有属性且这个属性的可枚举性为true 才返回true。
	
使用`!==`判断一个属性是否是undefined：

	var o = {x:1}
	o.x !==undefined;  //true o中有属性x
	o.y !==undefined;  //false o中没有属性x
	o.toString !==undefined; //true o继承toString属性

## 对象序列化
JSON：JavaScript Object Notation ——JavaScript对象表示法

`JSON.stringify()` //序列化JavaScript对象
`JSON.parse()` //还原JavaScript对象

##对象方法
`toString()`  返回一个表示调用这个方法的对象值的字符串
`toLocaleString()`  返回一个表示这个对象的本地化字符串
`toJSON()`
`valueOf()`

