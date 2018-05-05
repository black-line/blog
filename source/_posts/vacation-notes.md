title: Vacation-notes
date: 2016-02-03 17:13:34
tags:
---
闲来无事,写写笔记
看看Django,了解Python
开发环境:Ubuntu 14.04
知道了Python有三宝:pip,virtualenv,[没用过,留着]
<!--more-->
`pip`是Python的包管理工具,建议Python的包都用pip管理
`virtualenv`是Python多版本管理利器,用于不同版本的开发调试
[virtualenv userguide (英文版)](https://virtualenv.pypa.io/en/latest/userguide.html)
[virtualenv 1.7.1.2.post1 documentation (中文版)](http://virtualenv-chinese-docs.readthedocs.org/en/latest/#id29)
**安装pip** `$ sudo apt-get install python-pip`
- 缺pip命令

**安装virtualenv** `$ sudo pip install virtualenv`
- 缺命令

知道了virtualenv默认虚拟出来的环境是用于virtualenv安装的Python环境,因此，使用`$ (sudo) virtualenv --python=python3.4 env3.4`能虚拟Python3.4的环境。切换到环境目录下,运行`$ source bin/activite`,运行`$ deactivate`切换回原环境。
**安装Django** `$ (sudo) pip install Django`
创建工程,命名为mySite
`$ django-admin.py startproject mySite`
进入mySite启动工程
`$ cd mySite`
`$ python manage.py runserver`
在浏览器中打开http://localhost:8000/ 看到 “It worked!“，就表明已经安装好了。
[Django教程 (中文版)](http://www.ziqiangxuetang.com/django/django-install.html)