title: Linux下OBS安装
date: 2015-10-28 12:33:14
tags: [OBS, Linux, douyu]
---

##### 我要当主播
---

本来想在熊猫tv上开直播的，后来因为熊猫tv邮箱验证存在错误，所以选择斗鱼tv。毕竟作为曾经红火一时的直播平台，各方面都经受过考验。
_ _ _
<!--more-->
[申请直播间的故事](http://www.douyutv.com/cms/zhibo/201412/26/324.shtml)就不多说了。
++ 在Ubuntu15.04上安装OBS++
[Open Broadcaster Software 官方链接](https://obsproject.com/) 
**Free, open source software for live streaming and recording**

![](/images/OBSWithLinux.png)

在这里 如果按
```sudo add-apt-repository ppa:kirillshkrogalev/ffmpeg-next```
```sudo apt-get update && sudo apt-get install ffmpeg```
```sudo add-apt-repository ppa:obsproject/obs-studio```
```sudo apt-get update && sudo apt-get install obs-studio```
步骤会报错
我的安装过程是
```sudo add-apt-repository ppa:kirillshkrogalev/ffmpeg-next```
```sudo apt-get install ffmpeg```
```sudo add-apt-repository ppa:obsproject/obs-studio```
```sudo apt-get install obs-studio```
这样，就愉快的装好了。
![](/images/OBSWithLinux_2.png)
[开始愉快的直播吧](www.douyutv.com/cms/zhibo/201311/13/250.shtml)