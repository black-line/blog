title: Ubuntu 常用
date: 2015-12-24 18:43:45
tags:
---
##### UFW(Ubuntu 防火墙)
因为有一个部署在阿里云上的虚拟主机，现在开始用了，要注意**安全**，开始研究firewall。环境还是Ubuntu。

Linux原始的防火墙工具iptables由于过于繁琐,所以ubuntu系统默认提供了一个基于iptable之上的防火墙工具ufw。

###### 基础设置
一般用户，只需如下设置：
1.安装
$ sudo apt-get install ufw
2.启用
$ sudo ufw enable
$ sudo ufw default deny
运行以上两条命令后，开启了防火墙，并在系统启动时自动开启。关闭所有外部对本机的访问，但本机访问外部正常。
3.查看防火墙状态
$ sudo ufw status

<!--more-->
##### .deb包
一种预编译软件包。deb包中除了包含已编译的软件，通常还包括软件的拷贝路径、对其它软件包的依赖关系记录、一个比较通用的配置文件以及软件的描述、版本、作者、类别、占用空间等信息。
deb软件包命名遵行如下约定：
soft_ver-rev_arch.deb
soft为软件包名称，ver为软件版本号，rev为Ubuntu修订版本号，arch为目标架构名称。

* dpkg -i package.deb		安装包
* dpkg -r package               删除包
* dpkg -P package               删除包(包括配置文件)
* dpkg -L package		列出与该包关联的文件
* dpkg -l package		显示该包的版本
* dpkg --unpack package.deb     解开deb包的内容
* dpkg -S keyword		搜索所属的包内容
* dpkg -l			列出当前已安装的包
* dpkg -c package.deb		列出deb包的内容
* dpkg --configure package	配置包

##### apt命令
* $ apt-cache search package		                搜索软件包
* $ apt-cache show package	                 	获取包的相关信息(说明、大小、版本)
* $ sudo apt-get intsall package	                	安装包
* $ sudo apt-get intsall package --reinstall		重新安装包
* $ sudo apt-get -f install                               修复安装
* $ sudo apt-get remove package                           删除包
* $ sudo apt-get remove package --purge                   删除包，包括配置文件等
* $ sudo apt-get update                                   更新源
* $ sudo apt-get upgrade                                  更新已安装的包
* $ sudo apt-get dist-upgrade                             升级系统
* $ apt-cache depends package                             了解使用该包依赖哪些包
* $ apt-cache redepends package                           查看该包被哪些包依赖
* $ sudo apt-get build-dep package                        安装相关的编译环境
* $ apt-get source package                                下载该包的源代码
* $ sudo apt-get clean && sudo apt-get autoclean          清理无用的包
* $ sudo apt-get check                                    检查是否有损坏的依赖
