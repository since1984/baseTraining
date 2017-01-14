# Javascript基本功
## 正则表达式
### 基本语法
* /pattern/attributes
* new RegExp(pattern,attributes)

pattern : 正则表达式

attributes: i/g/m

* i: 不区分大小写
* g: 全局匹配
* m: 多行匹配

### 元字符

* . 查找单个字符，除了换行和结束符
* \w 查找单词字符 **[a-b0-9_]**
* \W 查找非单词字符 **[^a-b0-9_]**
* \d 查找数字 **[0-9]**
* \D 查找非数字 **[^0-9]**
* \s 查找空白字符
* \S 查找非空白字符
* \b 单词边界匹配
* \B 匹配非单词边界
* \0 查找NUL字符
* \n 换行符
* \f 换页符
* \r 回车符
* \t 制表符
* \v 垂直制表符
* \xxx 八进制 xxx规定字符
* \xdd 十六进制 dd规定字符
* \uxxxx 十六进制 xxxx规定unicode字符

### 量词
* n+ 至少一个n **{1,}**
* n* 0或多个n，不建议用 **{0,}**
* n? 0或1个n，**{0,1}**
* n{x} x个n
* n{x,y} x至y个n
* n{x,} 至少x个n
* n$ n结尾
* ^n n开始
* ?=n 匹配任何其后紧跟字符串n的字符串
* ?!n 匹配任何其后没有紧跟字符串n的字符串

### 正则属性
* global 对象是否具有标记g
* ignoreCase 对象是否具有标记i
* lastIndex 整数，标记下一个匹配字符位置
* multiline 对象是否具有标记m
* source 正则表达式的源文本

### 正则方法
* ~~compile 编译正则~~
* exec 检索字符串中指定的值，返回找到的值，并确定其位置
* test 检索字符串中指定的值，返回true或false

### 正则表达式相关String方法
* match
* search
* replace
* split