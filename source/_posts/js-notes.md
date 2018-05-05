title: Js学习笔记
date: 2015-11-21 11:20:04
tags: [Js, notes]
---
```
<script type="text/javascript" src="script.js">
</script>
var xxx+"xxx"; 弱类型
document.write("<br>"); 换行
confirm(""); 确认对话框(return Boolean)
prompt(str1, str2) 消息对话框 str1显示内容不可改 str2文本框内容可改 确认返回文本内容 取消返回NULL
window.open([URL], [窗口名称], [参数字符串])
参数说明:
URL：可选参数，在窗口中要显示网页的网址或路径。如果省略这个参数，或者它的值是空字符串，那么窗口就不显示任何文档。
窗口名称：可选参数，被打开窗口的名称。
1.该名称由字母、数字和下划线字符组成。
2."_top"、"_blank"、"_selft"具有特殊意义的名称。
   _blank：在新窗口显示目标网页
   _self：在当前窗口显示目标网页
   _top：框架网页中在上部窗口中显示目标网页
3.相同 name 的窗口只能创建一个，要想创建多个窗口则 name 不能相同。
4.name 不能包含有空格。
参数字符串：可选参数，设置窗口参数，各参数用逗号隔开。
参数表:
```
![](/images/JsWindowOpen.jpg)
<!--more-->
```
window.close() / mywin=window.open().close()(关闭窗口)
document.getElementById("id") return null or [object HTMLParagraphElement]

Object.innerHTML="";  获取或替换 HTML 元素的内容
Object.style.property="new style"; 改变HTML样式
background**C**olor font-**F**amily font**S**ize
```
![](/images/JsObjectStyleProperty.jpg)
```
object.className = classname 获取元素的class属性或为网页内的某个元素指定一个css样式
var myarr=new Array(); //定义数组 myarr[0]
myarr.length 获取数组长度(可变)  那中间未赋值的是多少?????????
var myarr=new Array();  //先声明一维
for(var i=0;i<2;i++){   //一维长度为2
   myarr[i]=new Array();  //再声明二维
   for(var j=0;j<3;j++){ //二维长度为3
   myarr[i][j]=i+j;   // 赋值，每个数组元素的值为i+j
   }
 }
```
##### Js Action
![](/images/JsAction.png)
```
var = document.getElementById(“id”）.value 取值 或赋值
parseInt(a);函数可解析一个字符串,并返回一个整数
.toString();
```
#### Js 内置对象
###### Date
get/setDay() 星期
![](/images/JsDate.png)
###### String
stringObject.length; /.toUpperCase(); ./toLowerCase(); /.charAt(index) 返回指定位置字符(以字符串形式)若找不到返回空字符串
stringObject.indexOf(substring, startpos)如果要检索的字符串值没有出现，则该方法返回 -1
![](/images/JsStringObjectIndexOf.png)
stringObject.split(separator,limit) 将字符串分割为字符串数组，并返回此数组 若把空字符串 ("") 用作 separator，那么 stringObject 中的每个字符之间都会被分割
![](/images/JsStringObjectSplit.png)
stringObject.substring(starPos,stopPos) stopPos可选
