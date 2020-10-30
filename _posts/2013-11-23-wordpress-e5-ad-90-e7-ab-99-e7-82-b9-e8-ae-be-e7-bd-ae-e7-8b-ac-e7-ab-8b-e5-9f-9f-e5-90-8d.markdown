---
layout: post
title: wordpress子站点设置独立域名
date: 2013-11-23 19:59:22.000000000 +08:00
---

如何创建子站点，查看此处：


# [wordpress二级域名多站点设置](http://kongqia.com/17970.html "wordpress耳机域名多站点设置")

 

设置号二级域名后，剩下只需要将主域名与二级域名绑定即可；

需要使用这个插件：


# WordPress MU Domain Mapping

[点击下载](http://wordpress.org/plugins/wordpress-mu-domain-mapping/ "点击下载")

接下来说一下安装步骤：

1. 访问[该下载页面](http://wordpress.org/extend/plugins/wordpress-mu-domain-mapping/)并下载后。解压缩所下载的压缩包。
2. 将压缩好中的“sunrise.php”文件上传至 WPMU 站点的“wp-content”目录中。
3. 将压缩包中的“domain_mapping.php”文件上传至 WPMU 站点的“mu-plugins”目录中。
4. 修改“wp-config.php”文件中的一下代码：


> //define( ‘SUNRISE’, ‘on’ );

改为（没有则添加以下记录）：

> define( ‘SUNRISE’, ‘on’ );

1. 接下来，站点管理人员便可以在子站点中的仪表盘 > 工具 >“Domain Mapping”选项并进行设置了。
2. 设置好站点的 IP 地址。以后用户想自己映射域名的时候，在各自的“管理”菜单中就可以自行设置了。

未经允许不得转载：[空洽网](http://kongqia.com) » [wordpress子站点设置独立域名](http://kongqia.com/18068.html)


