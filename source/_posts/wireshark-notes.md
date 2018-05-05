title: Wireshark-notes
date: 2015-12-05 01:08:48
tags: [wireshark, notes]
---
### 安装
坎坷的安装过程 我的天。。
从[这里](https://www.wireshark.org/download.html)下载源码。
解压
`tar -xvf wireshark-2.0.0.tar.bz2`
检查wireshark的依赖关系
`cd wireshark-2.0.0`
`./config`
发现一堆问题。。。。。。。。。。。。。。。
<!--more-->
1. 缺少yacc (or bison or ...)`
-yacc(Yet Another Compiler Compiler)，是Unix/Linux上一个用来生成编译器的编译器（编译器代码生成器）。
解决
`sudo apt-get install flex bison`
2. 缺少Qt
解决
`sudo apt-get install libqt4-dev` -听说要Qt5但是qt4也能用
3.  缺少GTK+ 3
解决
`sudo apt-get install libgtk-3-dev`
4. 缺少pcap.h等文件
解决
[下载源码](http://www.tcpdump.org/#latest-release)libpcap-1.7.4.tar.gz
```
tar -xvf libpcap-1.7.4.tar.gz
cd libpcap-1.0.0.tar.gz
./configure
make
sudo make install
```
终于到了`./configure`没有问题 可以安装wireshark的时候
看到
安装Checkinstall以便管理您系统中直接由源代码编译安装的软件。
google一下
---

Checkinstall is an extremely useful tool that helps when installing software after their compilation.
When a software is compiled, the following well known commands are used:

`#./configure`
`#make`
`#make install`

There are two majors problems with this way of installing programs:
1.	The "make uninstall" command is very often not available and thus you cannot uninstall the program.
2.	You don't have any tracking of the installed program.
All these problems are solved with CheckInstall, which replaces "make install" as shown below.

`#./configure`
`#make`
`#checkinstall`

Checkinstall executes the "make install" command, creates a Debian package and installs it with the "dpkg -i" command. This new Debian package is copied on the hard drive at the same time. You can use this package on another computer without having to compile the software again.
As the install has been done with a Debian package, it is now possible to use all the dpkg commands such as "dpkg -L" to see the installed files of a software or "dpkg -r" to uninstall a program very easily.
Please note that like "make install", the checkinstall command must be launched by the root user.

To install CheckInstall:

sudo apt-get install checkinstall

---
简单来说。好处:
1. 因为`make uninstall`命令经常找不到，所以checkinstall便于卸载用源码编译的文件而不用让用户寻找软件安装目录
原因:
Checkinstall执行`make install`命令，创建一个Debian软件包，并用“dpkg -i来”命令进行安装。这种新的Debian软件包被创建在当前目录下。你可以在其他电脑上使用这个安装包，而无需重新编译软件。由于用Debian包安装，可以使用所有的dpkg命令，如`dpkg的-L`查看已安装的软件或`dpkg-r`很卸载程序。**注意**,就像`make install`一样，`checkinstall`必须在root权限下使用。
安装
`sudo apt-get install checkinstall`
---
经过漫长的等待，wireshark终于编译完成了
但是。。。。。。。
出于安全方面的考虑，普通用户不能够打开网卡设备进行抓包，wireshark不建议用户通过sudo在root权限下运行
wireshark为ubuntu（Debian）用户提供了一种在非root下的解决方法。
（详细解释可以参考：/usr/share/doc/wireshark-common/README.Debian）
具体步骤：
`sudo dpkg-reconfigure wireshark-common`
选择Yes
在组策略中会出现wireshark组，默认没有任何用户属于这个组，只需把特定的用户加入组中（需要注销后重新登录来使设置生效）
就可以以该用户来运行wireshark实时抓网络数据包
在wireshark组后添加用户,若用户名user
`sudo usermod -a -G wireshark user`
万万没想到。。wireshark-common没装。。也不知道哪一步出错了。。
查看apt-get中wireshark版本。老。
最后
`sudo add-apt-repository ppa:wireshark-dev/stable`
`sudo apt-get update; sudo apt-get install wireshark`
这样就更新到了最新的2.0.0版本。
再用之前提到的
`sudo dpkg-reconfigure wireshark-common`
`sudo usermod -a -G wireshark user`
注销重新登录就生效了。

直接复制 没看过供参考

---

但是用ppa安装后会出现一些有关权限的问题，可以用下面的方法解决：
If you run wireshark as a non root user at this stage (see image above), you will get the message “No interface can be used for capturing in this system with the current configuration.”. The following steps will rectify this.

Create the wireshark group.

`sudo groupadd wireshark`
Add your username to the wireshark group
`sudo usermod -a -G wireshark YOUR_USER_NAME`
Change the group  ownership of file dumpcap to wireshark
`sudo chgrp wireshark /usr/bin/dumpcap`
Change the mode of the file dumpcap to allow execution by the group wireshark
`sudo chmod 750 /usr/bin/dumpcap`
Grant capabilities with setcap
`sudo setcap cap_net_raw,cap_net_admin=eip /usr/bin/dumpcap`
Verify the change
`sudo getcap /usr/bin/dumpcap`
At this point, you will need to log out, then back into Unity (Thanks for Jorge for pointing this out).
方法三：如果想装最新的wireshark版本，可以用下面的ppa:
The latest Wireshark version available is Wireshark 1.11.0, which can be installed from a PPA. To install Wireshark on Ubuntu, Linux Mint and Debian, do this:

`$ sudo add-apt-repository ppa:dreibh/ppa`
`$ sudo apt-get update`
`$ sudo apt-get install wireshar`
To start wiresharking, just type nohup wireshark &> /dev/null & in your terminal.

---

Ctrl-F -打开Find Packet
1.Display filter -输入表达式筛选 not ip,ip.addr==x.x.x.x,arp
2.Hex value -00:ff,ff:ff,00:AB:B1:f0
3.String -UserB,domin
将某一个数据包设定为时间参考 -选中数据包 Set Time Reference
### 过滤器
#### 捕获过滤器(BPF(Berkeley Packet Filter)语法)
**Ubuntu 14.10用不了？？？？**
限定词|说明|例子
---|---|---
Type|指出名字或数字所代表的意义|host,net,port
Dir|指明传输方向是前往还是来自名字或数字|src,dst
Proto|限定所要匹配的协议|ether,ip,tcp,udp,http,ftp
Ex: `dst host 192.168.0.10 && tcp port 80`
三种逻辑运算符: `&&   ||    !`
#### 显示过滤器
and or not xor(有且只有一个条件被满足)
___
Statistics->Endpoints -查看端口(端点地址，传输发送数据包的数量和字节数)
Statistics->Conversations -查看网络会话()
