title: Python学习笔记
date: 2015-11-10 22:45:38
tags: [python, notes]
---
### 基础
xx = input("提示语句")   xx为字符串类型 int(xx)转换为int
dir(\__builtins\__) 在Shell查看Bilt-in Function
help(input) 查看帮助
print("let's go") 不用转义
r'C:\now' 原始字符串，\n不转义 原理是自动添加反斜杠 但原始字符串末尾不能加\(可以r'xxx'+'\\')
`print("qwew", len(each),end=' ')` 结尾空格
长字符串(三引号)
str = '''
xx
xxxxx
xx
''' 自动添加\n 可在Shell看出
<!--more-->
逻辑操作符
`and` 等同于 `&` `or` `not`
类型转换
`int()` `float()` `str()`
运算
`/`真正除法 `//`取整 `**` 幂运算
三元操作符
	
    x,y=4,5
    if x < y:
    	small=x
    else:
    	small=y
等同与
`small=x if x < y else y`
`for i in "xxxx"
###### 列表(栈)
`list1.append` -末尾添加一个元素
`list1.extend` -末尾添加一个列表
`list1.insert` -在index位置添加一个元素或列表
`list1.remove` -移除一个指定列表中元素
`list1.pop` -不带参数时弹出末尾元素，带参数index.弹出.
`list1[a:b]` -复制index为[a,b)的元素 `[]`得到列表拷贝 不改变列表本身
`list1.count` -统计元素出现次数
`list1.index` -返回元素出现的index /(object,a,b) a -起始位置 b-终止位置
`list1.reverse` -逆置列表 改变列表本身
`list1.sort` -从小到大排序 /(func,key,reverse=False) func-指定排序算法 key-和算法搭配的关键字 默认归并排序
`list2==list1` - ~~_**错误**_~~
1.比较操作符
> < == 从0开始逐个比较
2.逻辑操作符
and....
3.连接操作符
+
4.重复操作符
*N -重复N次`list1` [a,b]*3 -> [a,b,a,b,a,b]
5.成员关系操作符
`xxx in list1` `xxx not in list1`
###### 元组(不可改变的列表)
(a,)*8 -> (a,a,a,a,a,a,a,a,a)
temp = (1,2,3) temp = temp[:1] + (4,) + temp[1:] temp -> (1,4,2,3) 间接插入
元组用切片进行间接删除
###### range()
`range({start,}stop[,step=1])` [start,stop) 不包括stop
###### assert
当assert后面条件为假时，程序自动崩溃并抛出AssertionError的异常
例:`assert 3 > 4` `assert False`
###### Random
`import random`
seed = random.randint(a,b) 范围[a,b]
###### isinstance
`from builtins import isinstance`
isinstance(object, class-or-type-or-tuple) -> bool
返回True或False
With a type as second argument, return whether that is the object's type.
如果使用tuple形式, isinstance(x, (A, B, ...))是isinstance(x, A) or isinstance(x, B) or ... (etc.)的简写**(没懂)**


### Re
记号 | 说明 | 样例
----|------|----
literal | 匹配字符串的值  | foo
re1|re2 | 匹配正则表达式re1或re2  | foo|bar
. | 匹配任意字符(换行符除外)  | b.b
^ | 匹配字符串的开始  | ^Dear
$ | 匹配字符串的结尾  | /bin/*sh$
* | 匹配前面出现的正则表达式零次或多次  | [A-Za-z0-9]*
+ | 匹配前面出现的正则表达式一次或多次  | [a-z]+\.com
? | 匹配前面出现的正则表达式零次或一次  | goo?
{N} | 匹配前面出现的正则表达式N次  | [0-9]{3}
{M,N} | 匹配重复出现M次到N次的正则表达式  | [0-9]{5,9}
[...] | 匹配字符组里出现的任意一个字符  | [aeiou]
[..x-y..] | 匹配从字符x到y中的任意一个字符  | [0-9],[A-Za-z]
[^...] | 不匹配此字符集中出现的任何一个字符,包括某一范围的字符  | [^aeiou],[^A-Za-z0-9_]
(*|+|?|{})? | 用于上面出现的任何"非贪婪".版本重复匹配次数符号  | .*?[a-z]
(...) | 匹配封闭括号中正则表达式(RE),并保存为子组  | ([0-9]{3})?,f(oo|u)bar

特殊字符

记号 | 说明 | 样例
----|------|----
\d | 匹配任何数字,和[0-9]一样 (\D是\d的反义: 任何非数字符) | data\d+.txt
\w | 匹配任何数字字母字符,和[A-Za-z0-9_]相同 (\W是\w的反义)  | [A-Za-z_]\w+
\s | 匹配任何空白符,和[\n\t\r\v\f]相同 (\S是\s的反义)  | of\sthe
\b | 匹配单词边界 (\B是\b的反义)  | \bThe\b
\nn | 匹配已保存的子组 (参考(...))  | price:\16
\c | 逐一匹配特殊字符c (即:按字面匹配)  | \.，\\，\*
\A(\Z) | 匹配字符串的起始(结束)  | \ADear

<!--more-->




![](/images/PythonRe.png)
(.+)? 无限贪  .+? 不贪
### os
`os.remove(path)` -删除文件(import os)
`os.rmdir(path, *, dir_fd=None)` -删除目录。只适用于目录是空的，否则，引起OSError异常。若递归删除目录，调用shutil.rmtree()
`os.path.isdir(path)` -如果目录存在返回true
`os.mkdir()` -创建一个名为path目录，若存在返回OSError
`os.makedirs(name, mode=0o777, exist_ok=False)` -递归创建目录，若存在返回OSError
`os.chdir(path)` -切换到path目录
`os.getcwd()` -返回当前工作目录的字符串
`os.path.join(path, *paths)` -智能联结一个或多个path 返回值是路径的串联和*path的任何成员与一个目录分隔符(The return value is the concatenation of path and any members of *paths with exactly one directory separator (os.sep) following each non-empty part except the last, meaning that the result will only end in a separator if the last part is empty. If a component is an absolute path, all previous components are thrown away and joining continues from the absolute path component.)
