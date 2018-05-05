title: 配置pppd拨号
date: 2015-11-09 10:08:29
tags: [Ubuntu, pppd拨号]
---
因为一些误判，我以为gnome-screenshot坏了，所以我将Ubuntu从15.04->15.10，为什么从网上找资料的时候都说Ubuntu可以用图形界面设置pppoe，但是我怎么不行啊
之前在15.04用pppoeconf配置过，所以有些文件还残留着。。。
<!--more-->
编辑 
`/etc/ppp/ip-up 添加 route and default dev ppp0`
然后就是熟悉的
`sudo pon dsl-provider  sudo poff`
