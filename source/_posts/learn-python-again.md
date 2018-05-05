title: 寒假开始啦～～
date: 2016-01-23 20:27:50
tags:
---
- long time no see
<!--more-->

#### 快速入门

1.1**字符串替换**
`print("%d + %f = %s" % (1,1.0,"2.0"))`
1.2**除法**
`//`整除 `3//1.1=2.0`
`/`真正除法 `3/1.1=2.72727272727`
1.3**逻辑操作符**
`and` `or` `not`

```
>>> '-' * 20
'--------------------'
```
1.4**if语句**
```
if 1:
    pass
elif 1:
    pass
else:
    pass
```
1.5**字符串索引 print不换行**
```
char = 'abcdefghijklmn'
for c in range(len(char)):
    print(char[c],end=' ')
print()
```
```
a b c d e f g h i j k l m n
```
1.6**列表解析**
```
spdEvens = [x ** 2 for x in range(8) if not x % 2]
for i in spdEvens:
    print(i, end=' ')
```
```
0 4 16 36
```


**#注释**单行注释
**分号;**将两个语句连接在一行中
`print("1");print("2")`
**反斜杠\**继续上一行(推荐使用括号)

```
if (weather_is_hot == 1) and \
        (shark_warnings == 0):
    print("HELP")
```

**多行书写**
在使用闭合操作符时，单一语句可以跨多行。
例如在含有小括号`()`，中括号`[]`，花括号`{}`时可以多行书写。在三引号`'''`包括下的字符串也可以跨行书写

```
print('''Hello
everyone''')
```
输出
```
Hello
everyone
```
同时赋值
`weather_is_hot, shark_warnings = (1,0)`
**变量赋值**
对象通过引用传递。在赋值时，不管这个对象是新创建的，还是一个已经存在的，都是将该对象的引用赋值给变量
赋值语句没有返回值，可以链式赋值
```
x = 1
y = x = x + 1
print(x,y)
```
输出
```
2 2
```
交换赋值
Pyrhon在赋值前已经事先对x和y的新值做了计算
```
x, y = 1, 2
print(x,y)
x, y = y, x
print(x, y)
```
输出
```
1 2
2 1
```