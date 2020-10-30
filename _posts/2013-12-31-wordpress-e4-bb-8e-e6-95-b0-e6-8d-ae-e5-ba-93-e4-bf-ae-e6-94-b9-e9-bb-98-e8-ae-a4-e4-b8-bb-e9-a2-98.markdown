---
layout: post
title: wordpress从数据库修改默认主题
date: 2013-12-31 07:06:00.000000000 +08:00
---

打开phpMyAdmin，选择对应的数据库，在sql文本框中输入以下查询语句，则看到当前的主题（theme）。

> SELECT *
> 
> FROM wp_options
> 
> WHERE option_name = ‘template’
> 
> OR option_name = ‘stylesheet’
> 
> OR option_name = ‘current_theme';

结果如下：

[![2](http://kongqia.com/wp-content/uploads/2013/12/2.png)](http://kongqia.com/wp-content/uploads/2013/12/2.png)将对应的红色字段修改为我们的主题名称即可。

未经允许不得转载：[空洽网](http://kongqia.com) » [wordpress从数据库修改默认主题](http://kongqia.com/31939.html)


