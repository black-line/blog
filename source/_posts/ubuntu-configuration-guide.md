---
title: ubuntu配置指南
date: 2017-03-15 15:42:21
tags: ubuntu
---
### Based on Ubuntu 16.04.02 LTS
Last updated: 2017-04-04

---
#### amule
[Welcome to aMule, the all-platform eMule-like P2P client](http://www.amule.org/)
```bash
$ sudo apt install amule
```
**TO BE CONTIUNE>>>** removed
<!--more-->
#### android studio
[Install Android Studio 2.0, Via PPA On Ubuntu 16.04](http://sourcedigit.com/19447-19447/)

Once Java is installed, run the following commands to install Android Studio:
```bash
$ sudo add-apt-repository ppa:paolorotolo/android-studio
$ sudo apt update
$ sudo apt install android-studio
```
If "Error: Unable to run mksdcard SDK tool" appeared
```bash
$ sudo apt install lib32stdc++6
```

#### chrome
[How to Install Google Chrome Web Browser in Ubuntu 14.04 LTS Trusty Tahr](http://ubuntuportal.com/2014/04/how-to-install-google-chrome-web-browser-in-ubuntu-14-04-lts-trusty-tahr.html)
```bash
$ wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
$ sudo sh -c 'echo "deb [arch=amd64] https://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
$ sudo apt update && sudo apt install -f
$ sudo apt install google-chrome-stable
```

#### clion
[https://www.jetbrains.com/help/clion/](https://www.jetbrains.com/help/clion/)
```bash
$ wget https://www.jetbrains.com/clion/download/download-thanks.html
```
*unpack*
```bash
$ tar xzvf /home/watermelon/Downloads/CLion-*
```
... ...
```bash
$ sh *.sh
```

#### dislocker
[1. Use (Windows) BitLocker-encrypted drive on Ubuntu 14.04 LTS](http://askubuntu.com/questions/617950/use-windows-bitlocker-encrypted-drive-on-ubuntu-14-04-lts "Use (Windows) BitLocker-encrypted drive on Ubuntu 14.04 LTS")

[2. FUSE driver to read/write Windows' BitLocker-ed volumes under Linux / Mac OSX](https://github.com/Aorimn/dislocker/tree/develop "FUSE driver to read/write Windows' BitLocker-ed volumes under Linux / Mac OSX")

[udisksctl - a new way to unmount and power off](http://unix.stackexchange.com/questions/178638/eject-safely-remove-vs-umount "udisksctl - a new way to unmount and power off")
```bash
$ git clone https://github.com/Aorimn/dislocker.git
$ sudo apt update
$ sudo apt install gcc cmake make libfuse-dev libmbedtls-dev ruby-dev
$ cmake .
$ make
$ sudo make install
```
example:
```bash
$ sudo dislocker -v -V /dev/sdc5 -u -- /media/bitlocker/
$ sudo mount /media/bitlocker/dislocker-file /media/mount/
```
...
```bash
$ umount /media/mount
$ umount /media/bitlocker
$ udisksctl unmount -b /dev/sdc1
$ udisksctl unmount -b /dev/sdc2
$ udisksctl unmount -b /dev/sdc3
$ udisksctl unmount -b /dev/sdc4
$ udisksctl unmount -b /dev/sdc5
$ udisksctl unmount -b /dev/sdc6
$ udisksctl unmount -b /dev/sdc7
$ udisksctl power-off -b /dev/sdc

```

#### ffvpn
[http://www.feifan-vpn.net/download-linux](http://www.feifan-vpn.net/download-linux)
```bash
$ tar -zxvf THE-DOWNLOADED-TAR-GZ
$ sudo vim /etc/ffvpn.conf
```
```vim
user YOUR-ACCOUNT-NAME
pass YOUR-PASSWORD
```
```bash
$ ./ffvpn login
$ ./ffvpn list
$ ./ffvpn list "usa"
$ ./ffvpn connect "California 13"
```
**Please choose protocol [udp/tcp/lwip/socks5]: socks5**

close google-chrome
```bash
$ google-chrome --proxy-server="socks5://127.0.0.1:1080"
```

#### git
[How To Install Git on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-16-04)
```bash
$ sudo apt update
$ sudo apt install git
$ git config --global user.name "Your Name"
$ git config --global user.email "youremail@domain.com"
$ git config --list
```

#### hadoop-2.7.2-compile
**install java7(may cause error with java8)**
```bash
$ sudo add-apt-repository ppa:webupd8team/java
$ sudo apt update
$ sudo apt install oracle-java8-installer
```
**install maven**
```bash
$ sudo apt install maven
$ mvn --version
```
**install dependciii**
```bash
$ sudo apt install g++ autoconf automake libtool cmake zlib1g-dev pkg-config libssl-dev
```
**install openssh**
```bash
$ sudo apt install openssh-server
```
**install Protocol Buffer**
```bash
$ wget ftp://ftp.netbsd.org/pub/pkgsrc/distfiles/protobuf-2.5.0.tar.gz -O protobuf-2.5.0.tar.gz
$ tar xvf protobuf-2.5.0.tar.gz
$ cd protobuf-2.5.0/
$ ./configure
$ make
$ make check
$ sudo make install
$ sudo ldconfig
```
important!!!

**compile hadoop**

In order to prevent the Java memory overflow within the compilation process, we need add the following environment variables
```bash
$ vim /etc/profile
```
```vim
export MAVEN_OPTS="-Xmx2048m -XX:MaxPermSize=512m"
```
```bash
$ source /etc/profile
$ wget http://apache.01link.hk/hadoop/common/hadoop-2.7.2/hadoop-2.7.2-src.tar.gz -O hadoop-2.7.2-src.tar.gz
```
(not the only source)
```bash
$ tar xvf hadoop-2.7.2-src.tar.gz
$ cd hadoop-2.7.2-src/
$ mvn clean package -Pdist,native -DskipTests -Dtar
```

#### hexo
[https://hexo.io/docs/](https://hexo.io/docs/)
```bash
$ sudo apt install git
$ wget -qO- https://raw.githubusercontent.com/creationix/nvm/master/install.sh | sh
```
Once nvm is installed, restart the terminal and run the following command to install Node.js.
```bash
$ nvm install stable
$ npm install -g hexo-cli
```
there are two warnings:
1. npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@^1.0.0 (node_modules/hexo-cli/node_modules/chokidar/node_modules/fsevents):

2. npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.1.1: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})

#### hit-oslab
[操作系统实验报告-熟悉实验环境](http://www.cnblogs.com/tradoff/p/5693710.html)

#### hosts
[racaljk/hosts: 最新可用的google hosts文件. 镜像: https://coding.net/u/scaffrey/p/hosts/git](https://github.com/racaljk/hosts)

or 

[https://raw.githubusercontent.com/racaljk/hosts/master/hosts](https://raw.githubusercontent.com/racaljk/hosts/master/hosts)

copy all
```bash
$ cd /etc
$ sudo cp hosts hosts.bak
$ sudo vi hosts
```
->...... (restart)

https://www.google.com/ncr

#### htop
[1. Using htop to Monitor System Processes on Linux](http://www.howtogeek.com/howto/ubuntu/using-htop-to-monitor-system-processes-on-linux/)

[2. How to Manage Processes from the Linux Terminal: 10 Commands You Need to Know](http://www.howtogeek.com/107217/how-to-manage-processes-from-the-linux-terminal-10-commands-you-need-to-know/)
```bash
$ sudo apt install htop
```

#### ibus-pinyin
[英文版ubuntu安装ibus输入法(中文输入法)和开机自启动的方法](http://www.jb51.net/os/Ubuntu/161244.html)
```bash
$ sudo apt install ibus-pinyin
```
restart

System Settings-> Text Entry-> press "+"-> find Chinese(Pinyin)(IBus)

press "add"

#### java8
[1. Installing JAVA jre/jdk with Ubuntu 16.04](https://www.unixmen.com/installing-java-jrejdk-ubuntu-16-04/)

[2. Install Oracle Java On Ubuntu 16.04, via Terminal](http://sourcedigit.com/19575-install-oracle-java-on-ubuntu-16-04-via-terminal/)

Before you begin the installation, run the following command to verify the version of Java already installed on the system.
```bash
$ java -version
```
```bash
$ sudo add-apt-repository ppa:webupd8team/java
$ sudo apt update
$ sudo apt install oracle-java8-installer
```
If you have more than one different flavors of Java installed, we can find appropriate path for java version we want to make default
```bash
$ sudo update-alternatives --config java
```
Open and edit /etc/profile file
```bash
$ sudo vim /etc/profile
```
Put following line in last line of the file, copy jre path from previous command:
```vim
export JAVA_HOME="/usr/lib/jvm/java-8-oracle"
export PATH="${PATH}:${JAVA_HOME}/bin"
```
```bash
$ source /etc/profile
```
Verify default JAVA_HOME is effectively modified or not
```bash
$ echo $JAVA_HOME
```

#### latex
[LaTeX Tutorial – Interactive Lessons, Code Examples – For Beginners](https://www.latex-tutorial.com/)
```bash
$ sudo add-apt-repository ppa:jonathonf/texlive
$ sudo apt update
$ sudo apt install texlive-full texmaker
```

#### markdown
[MOEDITOR Your all-purpose markdown editor.](https://moeditor.org/)

example:
```bash
$ wget https://github.com/Moeditor/Moeditor/releases/download/v0.2.0-beta/moeditor_0.2.0-1_amd64.deb
$ sudo dpkg -i moeditor_0.2.0-1_amd64.deb
```

#### matlab
[Ubuntu16.04下 Matlab2015b安装与激活及注意事项](http://blog.csdn.net/lcx543576178/article/details/51376008)
```bash
$ sudo ln -s /usr/local/MATLAB/R2015b/bin/matlab   /usr/local/bin/matlab
```

#### my cloud ex2 ultra
For WD My Cloud, there is no official support for  Ubuntu or any other Linux distros. But setting up it quite easy.

Make sure You have connected power adapter & LAN cables to it. If You open Your router config, You will see WD My cloud in client list. Make note of its IP address. If You want You can assign a static IP also.

Next step is to install NFS client package. NFS(Network File System) allows a system to share directories and files with others over a network. By using NFS, users and programs can access files on remote systems almost as if they were local files. So, update your packages & install nfs-common package.
```bash
$ sudo apt update
$ sudo apt install nfs-common
$ showmount -e <ip-address>
$ sudo mount -o rw,soft,intr,nfsvers=3 <ip>:<folder-to-mount> <path-to-mount>
```
example:

(sudo mount -o rw,soft,intr,nfsvers=3 192.168.1.5:/mnt/HD/HD_a2/jessywu ~/wdmceu/)

#### opencv
[Installation in Linux — OpenCV 2.4.13.0 documentation](http://docs.opencv.org/2.4.13/doc/tutorials/introduction/linux_install/linux_install.html#linux-installation)

#### opengl
[Ubuntu 16.04 OpenGL 开发环境配置指南](http://www.jianshu.com/p/e4a90503d4a6)
```bash
$ sudo apt install build-essential libgl1-mesa-dev
$ sudo apt install freeglut3-dev
$ sudo apt install libglew-dev libsdl2-dev libsdl2-image-dev libglm-dev libfreetype6-dev
```

#### pppoe
```bash
$ sudo pppoeconf
```

#### python
[User Guide — virtualenv 15.2.0.dev0 documentation](https://virtualenv.pypa.io/en/latest/userguide/)

[How To Install Pip on Ubuntu 16.04](http://idroot.net/linux/install-pip-ubuntu-16-04/)

[Virtual Environments — Guide to Python](http://docs.python-guide.org/en/latest/dev/virtualenvs/)
```bash
$ sudo apt install python-pip
$ sudo -H pip install virtualenv
$ virtualenv -p /usr/bin/python3.5 venv
$ source venv/bin/activate
$ deactivate
```
way to duplicate virtualenv

go into your original virtualenv, and run:
```bash
$ pip freeze > requirements.txt
```
activate your new virtualenv, and run:
```bash
$ pip install -r requirements.txt
```

#### rar
[ubuntu解压命令全览(rar)](http://www.cnblogs.com/lotusve/archive/2012/05/16/2503388.html)
```bash
$ sudo apt install rar
$ sudo apt install unrar
```
example:
```bash
$ rar x FileName.rar
$ rar a FileName.rar DirName
```
针对Windows下zip在Linux下中文解压后显示乱码
```bash
$ sudo apt install unar
```

#### theme
[This is a Flat theme for Ubuntu and other Gnome based Linux Systems.](https://github.com/anmoljagetia/Flatabulous)
```bash
$ sudo apt-get install unity-tweak-tool

$ sudo add-apt-repository ppa:noobslab/themes
$ sudo apt-get update
$ sudo apt-get install flatabulous-theme

$ sudo add-apt-repository ppa:noobslab/icons
$ sudo apt-get update
$ sudo apt-get install ultra-flat-icons
```
> Now press your super key, search for Unity Tweak Tool and fire it. Under the tools tab, there is an option for theme. Under that select the Flatabulous theme. Under the icon settings, select ultra-flat-icons. Restart your computer, and you should be good to go!

#### tree
```bash
$ sudo apt install tree
```

#### turboC3
[教程: 使用dosbox安装、运行Turbo C++ 3.0(tc3)](http://forum.ubuntu.org.cn/viewtopic.php?t=69330)

run the following commands in DOSBox Emulator
```bash
mount c ~/dosapp
c:
cd tc\bin
tc
```
exit dosbox
```bash
exit
```

#### ufw
[Error_404_资源不存在](http://www.cnblogs.com/xiaofengkang/archive/2011/10/22/2220888.html)
```bash
$ sudo apt install ufw
$ sudo ufw enable
$ sudo ufw default deny
```

#### virtualbox
[Virtualbox 5.1 Released, How to Install in Ubuntu 16.04](http://ubuntuhandbook.org/index.php/2016/07/virtualbox-5-1-released/)

[Linux_Downloads – Oracle VM VirtualBox](https://www.virtualbox.org/wiki/Linux_Downloads)
```bash
$ sudo apt install dkms
$ sudo apt remove virtualbox virtualbox-5.0 virtualbox-4.*
$ sudo sh -c 'echo "deb http://download.virtualbox.org/virtualbox/debian xenial contrib" >> /etc/apt/sources.list.d/virtualbox.list'
$ wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
```
(B9F8 D658 297A F3EF C18D  5CDF A2F6 83C5 2980 AECF)
```bash
$ sudo apt update
$ sudo apt install virtualbox-5.1
```

#### vs code
[Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux)
```bash
$ curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
$ sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
$ sudo sh -c 'echo "deb [arch=amd64] http://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
$ sudo apt update
$ sudo apt install code
```

#### wifi
-> System Settings-> Software&Updates-> Additional Drivers->......

#### wine
```bash
$ sudo add-apt-repository ppa:ubuntu-wine/ppa
$ sudo apt update
$ sudo apt install wine1.8
```

#### xmind
[Download XMind for Linux - XMind: The Most Popular Mind Mapping Software on The Planet.](http://www.xmind.net/download/linux/)
```bash
$ sudo apt update
$ sudo dpkg -i xmind-xx-xx-xxxx.deb
$ sudo apt -f install
```
