title: 备战数据结构
date: 2015-10-14 13:59:35
tags: 结构体
---

好久没写C语言了， 现在要学数据结构。。

定义结构体如下：
```
struct student
{
	char name[10];
	int age;
	int score[5];
	int ave;
}Tom = {"Tom", 20, 78, 92, 83, 75, 69}， Bob， Lee;
```
其中， 虽然Tom.ave，Bob.ave均未赋初始值，但是Tom.ave值为0, 而Bob.ave值随机。
`Lee = Tom`可行
`Lee = {"Tom", 20, 78, 92, 83, 75, 69}` 报错

字符串拷贝
`strcpy(Tom.name, "ChangeName")` **这就是C**




