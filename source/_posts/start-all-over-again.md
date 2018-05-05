title: 重新开始
date: 2015-10-11 23:51:45
tags: [Start, Linux, Github, Eclipse]
---

# 我的十一回顾

国庆第一天，闲来无事，重新注册了一个github帐号，之前的帐号也许还记得，得找个时间把它删了，占人家github空间也不好。从美国回来有了一个gmail帐号和twitter帐号，准备和专业有关的都用这个帐号，毕竟gmail是最好用得邮箱。++~我大天朝..~++

[史上最浅显易懂的git教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
来自廖雪峰老师，挺不错的课程，**安利**一下，另外还有JS，python教程。

git教程学了几天，同步远程库，拷贝远程库。顿感Windows很不好用，估计是我之前乱装软件，很卡很慢，网页访问还有问题，累觉不爱。++换++！

拿着Seagate的protable drive，备份了两天。~(无奈电脑东西太多../可怕)~ & *sweet experience ~*
<!--more-->
## Linux
装linux，先试试Ubuntu，毕竟初试。
[Ubuntu 14.04 和 Windows 8.1 双系统安装步骤](http://os.51cto.com/art/201405/439158.htm)
安装过程不多说。

## Eclipse
重点来了。
由于时间紧迫，急需搭建编译环境，所以选择了IDE。
**java**:eclipse自带，不多说。
**Python**：Help -> Eclipse Marketplace -> PyDev
Ubuntu 自带Python既有2.X又有3.X，由于Ubuntu运行需要2.X环境，所以2.X不能移除。要更改Eclipse默认选择。
Windows -> Preferences -> PyDev -> Interpreters -> Python Interpreter 选择Advanced Auto-Config 相信会找到3.X
**C++**：Help -> Eclipse Marketplace -> CDT
++问题来了：++在多次尝试下载C++编译器Failed..虽然我没有配置编译器minGW，在新建C++ Project时惊喜发现Linux就有Linux GCC。over。
（注意在Run C++ Project 时要先Project -> Build Project）
**PHP**：php是我装的最纠结的。
Apache+Mysql+PhpMyAdmin
###### 安装 Apache `apt-get install apache2`
###### 安装PHP5 `apt-get install php5 libapache2-mod-php5`
###### 安装MySQL `apt-get install mysql-server`
由于PHP网络服务器根目录默认设置是在：/var/www。。由于Linux系统的安全性原则，该目录下的文件读写权限是只允许root用户操作的，所以我们不能在www文件夹中新建php文件，也不能修改和删除，必须要先修改/var/www目录的读写权限。执行命令：sudo chmod 777 /var/www。然后就可以写入html或php文件了。（如果对777表示的文件权限不是很清楚）以后补充
###### 安装PhpMyAdmin
	sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin
	cp /etc/phpmyadmin/apache.conf /etc/apache2/sites-enabled/phpmyadmin
在安装过程中会要求选择Web server：apache2或lighttpd，选择apache2
完成后，将Eclipse 的workspace，phpmyadmin与www关联，以我为例，

    sudo ln -s /usr/share/phpmyadmin /var/www/html
    sudo ln -s /home/username/workspace /var/www/html
###### 开启rewrite模块 `sudo a2enmod rewrite`
###### 重启APACHE `sudo /etc/init.d/apache2 restart`
###### 常用的几个命令
重启 apache：`sudo /etc/init.d/apache2 restart`

重启mysql：`sudo /etc/init.d/mysql restart`

配置 php.ini：`sudo gedit /etc/php5/apache2/php.ini`

配置 apache2.conf：`sudo gedit /etc/apache2/apache2.conf`

###### One more thing

在安装好lamp后，在安装phpmyadmin会有mysqli的丢失，其实不是应为没有安装相应的扩展，而是即使安装好扩展，但是apache和phpmyadmin不能找到，所以要手动配置一下:


第一步：到/usr/lib/php5/ 查找mysqli.so 发现在 /usr/lib/php5/20131226/下面
第二步：`sudo gedit /etc/php5/apache2/php.ini`

关于Ubuntu下安装phpmyadmin后mysqli丢失的解决
找到这两个地方
1.
``` 
; Directory in which the loadable extensions (modules) reside.
; http://php.net/extension-dir
; extension_dir = "./"
**extension_dir = "/usr/lib/php5/20131226"**
; On windows:
; extension_dir = "ext" ```

```
; If you wish to have an extension loaded automatically, use the following
; syntax:
;
;   extension=modulename.extension
;
; For example, on Windows:
;
;   extension=msql.dll
;
; ... or under UNIX:
;
**extension=msqli.so**
;
; ... or with a path:
```
第三步：`sudo service apache2 restart` 

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="http://music.163.com/outchain/player?type=2&id=3951392&auto=1&height=66"></iframe>
