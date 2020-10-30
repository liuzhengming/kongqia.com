---
layout: post
title: ubuntu 命令行连接无线网络
date: 2014-05-10 16:16:28.000000000 +08:00
---

ubuntu 命令行连接无线网络

1、生成无线路由密钥。

根据你无线网络的SSID和密码，来生成WLAN需要的配置文件。命令如下：

> wpa_passphrase 无线网络SSID 无线网络密码 > 配置文件名

比如你的无线网络SSID是TP-LINK，密码是123456，生成的配置文件名为wpa_config.conf，输入：

> wpa_passphrase TP-LINK 123456 > wpa_config.conf

wpa_config.conf的名称可以随便取。

2、设置无线网络。

编辑/etc/network/interfaces文件，将wlan添加到其中：

> sudo vim /etc/network/interfaces

在里面加上：

> auto wlan0  
>  iface wlan0 inet dhcp  
>  wpa-conf /home/您的用户名/wpa_config.conf

3、重新启动计算机，然后就可以使用了。

未经允许不得转载：[空洽网](http://kongqia.com) » [ubuntu 命令行连接无线网络](http://kongqia.com/33430.html)


