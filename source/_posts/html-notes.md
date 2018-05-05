title: Html学习笔记
date: 2015-11-15 21:20:50
tags: [Html, notes]
---

![](The-Little-Prince.gif)
```
style="font-size: 10px; font-family: Impact; color:red; background-color:brown; text-align:center"

<strong>加粗</strong>
<em>斜体</em>
<q>引用简短文本("xxxx")</q>
<blockquote>引用长文本(段落缩进样式)</blockquote>
<!--comments-->
&nbsp;(空格)
<hr />(添加水平横线)
<br />(换行)
<address>联系地址信息</address>
<code>代码语言</code>
<pre>多行代码</pre>(保留空格和换行符)

<table summary="">
<thead>
<tr><th colspan="2"></th></tr>     or <caption></caption>  猜。。
</thed>
<tbody>
<tr><td></td></tr>
<tr><td></td></tr>
</tbody>
</table>


<head><link type="text/css" rel="stylesheet" href="stylesheet.css"/></head>
or <head><style></style></head>

<a  href="目标网址"  title="鼠标滑过显示的文本" target="_blank">链接显示的文本</a>   链接在新窗口打开
```
<!--more-->
![](/images/MailTo.png)
![](/images/MailToEx.png)
<a href="mailto:yy@imooc.com?subject="观了不起的盖茨比有感"&body="你好，对此评论有些想法"">对此影评有何感想，发送邮件给我</a>
```
<img src="图片地址" alt="下载失败时的替换文本" title = "提示文本">
1、src：标识图像的位置；
2、alt：指定图像的描述性文本，当图像不可见时（下载不成功时），可看到该属性指定的文本；
3、title：提供在图像可见时对图像的描述(鼠标滑过图片时显示的文本)；
4、图像可以是GIF，PNG，JPEG格式的图像文件。

<ul></ul> <ol></ol> <li></li>



<div style="width:50px; height:50px; background-color: red"></div>

<span></span>

td {border: 1px dashed blue;}

去除超链接下划线`text-decoration: none;

div > p  div p 有区别

id #    class .
a: /link /hover /visited   伪选择器 事先text-decoration

p:first-child   //It's used to apply styling to only the elements that are the first children of their parents.

p:nth-cilld(x)  //select any child of an element after the first child with the pseudo-class selector nth-child

class id exist at the same time
```
![](/images/CSS-box-model.png)
#### Taking up space
```
display: /block(default) /inline-block(used in navigation bar) /inline /none
//any element
margin: /auto(equal left and right)
float:(You can think of the HTML page as sort of like a sea, and floating elements as boats on it: all the boats have positions on the sea, and they all see and steer clear of each other.)

clear: /left /right /both(immediately move below any floating elements )
position: /static(default) /absolute /relative /fixed  ?????????

z-index:1; (ensures that "xxx" will sit "on top of" your other elements)
```
#### meta
`<meta http-equiv="refresh" content="0;url=http://www.baidu.com/">` -过0秒自动跳转
