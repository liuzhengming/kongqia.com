---
layout: post
title: Ubuntu apt-get安装 mongodb
date: 2016-11-17 04:31:54.000000000 +08:00
---

### 通过apt-key增加MongoDB的公钥Key到本地Key数据库

**sudo apt-key adv –keyserver keyserver.ubuntu.com –recv 7F0CEB10**

**#Upstart  
 deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen**

### 编辑/etc/apt/sources.list,添加MongoDB软件源

vi /etc/apt/sources.list  
 #增加下面的软件源  
**deb http://downloads-distro.mongodb.org/repo/debian-sysvinit dist 10gen**

### 安装MongoDB

#更新本地软件包列表信息  
**apt-get update**  
 #安装MongoDB  
**apt-get install mongodb-10gen**

转至：http://blog.csdn.net/sasoritattoo/article/details/11978531

未经允许不得转载：[空洽网](http://kongqia.com) » [Ubuntu apt-get安装 mongodb](http://kongqia.com/33750.html)


