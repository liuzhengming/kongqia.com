---
layout: post
title: VPS搭建shadowsocks服务以及配置shadowsocks多用户
date: 2017-12-15 23:00:37.000000000 +08:00
---
介绍在VPS中（虚拟主机）搭建shadowsocks服务，从而实现科学上网，配置多个shadowsocks用户实现多用户共享。

1. 安装shadowsocks服务端

Ubuntu
`sudo apt-get install python-pip`

`sudo pip install shadowsocks` 

CentOS

`sudo yum install pip`

`sudo pip install shadowsocks`

2. 配置shadowsocks服务端配置文件

安装完成之后其实就可以执行命令来启动shadowsocks服务了。

`ssserver -p 8000 -k password -m rc4-md5 -d start`

配置文件内容

更好的意见是把选项写在一个配置文件中，然后通过读取这个配置文件来配置shadowsocks的行为。vi /path/to/your/config-file(注：配置文件放置的位置随意，我一般是放在 /etc/shadowsocks.conf )

单用户配置
```javascript
{
    "server":"你的VPS公网ip",
    "server_port":"你想shadowsocks监听的端口",
    "local_address":"127.0.0.1",
    "lcoal_port":1080,
    "password":"你想设置的密码",
    "method":"rc4-md5",  #加密算法还有其他的如aes-256-cfb，aes-128-cfb，速度快的话就选择rc4-md5
      "timeout":300
}
```
多用户配置
```javascript
{
  "server":"你的VPS公网ip",
    "local_address":"127.0.0.1",
    "lcoal_port":1080,
    "method":"rc4-md5",
    "timeout":300,
    "port_password":
    {
      "port1":"passwd1",
      "port2":"passwd2",
      ...
    }
}
```
开启shawosocks服务
`ssserver -c /etc/shadowsocks.conf --log-file=/tmp/shadowsocks.log -d start`

转至：
https://timlentse.github.io/2016/04/04/install-ss-service.html
