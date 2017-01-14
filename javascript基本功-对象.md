# javascript基本功
## 对象
### js对象的创建方式
* 工厂模式
* 构造函数模式
* 原型对象模式
* 混合构造函数和原型对象模式
* 动态原型模式
* 寄生构造函数模式
* 稳妥构造函数模式

### js继承的6种方法
* 原型链继承
* 借用构造函数继承
* 组合继承（原型+借用构造）
* 原型式继承
* 寄生式继承
* 寄生组合式继承


### 面向对象
* 只关注对象提供的功能，不关注其内部细节
* 面向对象是一种通用思想，并非只有编程中使用，任何事情都可以用

#### JS中的OOP
> （抽象：抓核心）

* 继承：从已有对象上，继承出新对象
	* 多重继承：有多个父级
	* 多态：父类和子类之间有相同的操作，但操作又不那么一样 
* 多态
* 封装：不考虑内部实现，只考虑功能使用

#### 构造函数
用来创建对象的函数
> 用工厂方式构造对象

问题

* 调用的时候没有new（var cc = createObj('tim','男')）
* 工厂方式内的方法在调用时不相等 cc.showname() != bb.showname()

~~~js
function createObj(param1,param2){
	// 原材料
	var obj = new Object();
	// 加工
	obj.name = param1;
	obj.sex = param2;
	obj.showname = function(){
		alert(this.name)
	}
	obj.showsex = function(){
		alert(this.sex)
	}
	// 出厂
	return obj;
}
~~~

> 解决new的问题

~~~js
function createObj(param1,param2){
	// new后系统默认执行原材料
	// var this = new Object();
	
	// 加工
	this.name = param1;
	this.sex = param2;
	this.showname = function(){
		alert(this.name)
	}
	this.showsex = function(){
		alert(this.sex)
	}
	// new后系统默认执行出厂
	// return this;
}

var cc = new createObj();
~~~

> prototype 解决方法不等的问题

~~~js
Array.prototype.sum = function(){
	
}
~~~

* 类
* 对象（实例）