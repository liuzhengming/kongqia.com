---
layout: post
title: mac 安装 composer
date: 2016-03-08 22:07:03.000000000 +08:00
---

使用 curl 下载：

> curl -sS https://getcomposer.org/installer | php

或使用 php 下载：

> php -r “readfile(‘https://getcomposer.org/installer’);” | php

当下载了 composer.phar 后，将它放到 usr/local/bin 目录中中，成为全域指令。

> mv composer.phar /usr/local/bin/composer

则就可以在终端使用composer命令了。

未经允许不得转载：[空洽网](http://kongqia.com) » [mac 安装 composer](http://kongqia.com/33696.html)


