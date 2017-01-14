# Javascript基本功
## 字符串操作
### 1. concat
* 将两个或多个字符串合并起来
* 返回一个新的字符串
* 等同有 str1 + str2

~~~js
var a = 'hello';
var b = ' world';
var c = ' heeh';

var result = a.concat(b,c);
=> hello world heeh
~~~

### 2. indexOf
* 返回字符串中一个子串第一次出现的索引
* 如果没有返回-1
* 从左向右查找

~~~js
var a = 'hello';
var result = a.indexOf('l');
=> 2
result = a.indexOf('l',3);
=> 3
result = a.indexOf('i');
=> -1
result = a.indexOf('lo');
=> 3
~~~

### 3. charAt
* 返回指定索引的字符
* -1或者大于字符长度均无返回值

> charCodeAt 查找对应位置的字符串编码值

~~~js
var a = 'hello';
var result = a.charAt(0);
=> h
~~~ 

### 4. lastIndexOf
* 返回字符串中一个子串最后一次出现的索引
* 如果没有返回-1
* 从右向左查找

### 5. match
* 检查一个字符串匹配一个正则表达式内容
* 如果没有返回null

> exec与match一样，但用法相反 patten.exec(myStr)

~~~js
var a = 'hello';
var b = ' world';
var c = "I,Love,You,Do,You,Love,Me";
var patten = /Love/;
var re = new RegExp(/^\w+$/);
var result = a.match(re);
=> ['hello']
result = b.match(re);
=> null
result = c.match(patten);
=>['Love']
console.log(result.index)
console.log(result.input)
=> 2
=> "I,Love,You,Do,You,Love,Me"
~~~

### 6. substring
* 返回一个字符串的子串
* 参数：起始位置，结束位置

~~~js
var a = 'hello';
var result = a.substring(1);
==> ello
result = a.substring(1,4)
==> ell 
~~~

### 7. substr
* 返回一个字符串的子串
* 参数：起始位置，长度

### 8. replace
* 用来查找匹配一个正则表达式字符串
* 用新字符串替换旧字符串

~~~js
var a = 'hello';
var b = ',world';
var c = "I,Love,You,Do,You,Love,Me";
var re = new RegExp(/^\w+$/);

var result = a.replace(re,'Hello');
=> Hello
var result = b.replace(re,'Hello');
=> hello
var result = c.replace('Love','Hate');
=> I,Hate,You,Do,You,Love,Me
var result = c.replace('/love/g','Hate')
=> I,Hate,You,Do,You,Hate,Me
~~~

### 9. search
* 用来查找匹配一个正则表达式字符串
* 返回字符串匹配的索引值
* 否则返回-1

~~~js
var a = 'hello';
var b = ',world';
var re = new RegExp(/^\w+$/);

var result = a.search(re);
=> 0
result = b.search(re)
=> -1
~~~

### 10.slice
* 提取字符串中的子串
* 参数：起始位置，结束位置
* 与substring不同
* 参数可以为负数，但依然从左向右查找

~~~js
var a = 'hello';
var b = ',world';

var result = a.slice(1,4);
=> ell
result1 = a.slice(-1);
result2 = a.substring(-1);
=> o
=> hello
result1 = a.slice(-1,10);
result2 = a.substring(-1,10);
=> o
=> hello
result1 = a.slice(-3,-1);
result2 = a.substring(-3,-1);
=> ll
=>
~~~

### 11.split
* 将字符串划分成子串
* 生成字符串数组
* 可带第二个参数，表示返回字符串数组的最大长度

~~~ js
var a = 'hello';
var b = 'he?ll?o';
var result = a.split('');
=>['h','e','l','l','o']
result = a.split('',3);
=>['h','e','l']
result = b.split('?');
=> ['he','ll','o'];
result = a.split('l');
=> ['he','','o'];
result = a.split('#');
=> ['hello']
~~~

### 12.toLowerCase
* 将字符串全部转换为小写

### 13.toUpperCase
* 将字符串全部转换为大写
### 14.trim
* 去除字符串前后空格

### 15.trimLeft
### 16.trimRight
### 17.toString
* 数值转换成字符串

~~~js
var num = 19;
var myStr = num.toString();
=> '19'
var myStr = String(num);
var myStr = num + '';
~~~

### 18.localeCompare
* 比较两个字符串
* 按字母顺序比较大小
* -1 小，0 等，1 大

~~~js
var myStr = "chicken";
var myStrTwo = "egg";
var first = myStr.localeCompare(myStrTwo); // -1
first = myStr.localeCompare("chicken"); // 0
first = myStr.localeCompare("apple"); // 1
~~~