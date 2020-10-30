---
layout: post
title: 'wordpress提示：Warning: Cannot modify header information – headers already sent
  by'
date: 2014-01-06 01:20:02.000000000 +08:00
---

[![warning](http://kongqia.com/wp-content/uploads/2014/01/1c950a7b02087bf4a4301611f3d3572c10dfcf6e.jpg.png)](http://kongqia.com/wp-content/uploads/2014/01/1c950a7b02087bf4a4301611f3d3572c10dfcf6e.jpg.png)

问题：在网站升级或搬家后出现以下错误：

> Warning: Cannot modify header information – headers already sent

问题根源：

在升级或搬家后wp-config.php文件造成编码错误，变成了UTF8含BOM。

解决办法：

使用Notepad++、UltraEdit、EditPlus等编辑器更改wp-config.php编辑文件，重新保存为UTF8无BOM就好了。

未经允许不得转载：[空洽网](http://kongqia.com) » [wordpress提示：Warning: Cannot modify header information – headers already sent by](http://kongqia.com/33105.html)


