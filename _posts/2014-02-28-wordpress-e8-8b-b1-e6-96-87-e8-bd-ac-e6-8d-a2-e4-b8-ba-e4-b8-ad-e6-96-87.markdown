---
layout: post
title: wordpress英文转换为中文
date: 2014-02-28 04:21:21.000000000 +08:00
---

[![u=102511570,3312890772&fm=23&gp=0.jpg](http://kongqia.com/wp-content/uploads/2014/02/u1025115703312890772fm23gp0.jpg.png)](http://kongqia.com/wp-content/uploads/2014/02/u1025115703312890772fm23gp0.jpg.png)

不留神安装了英文版wordpress？

别着急，有简单办法转换为中文的。

找到根目录下地wp-config.php，搜索define(‘WPLANG’；默认的英文样子：

> define(‘WPLANG’, ”);

要改成中文的，讲以上代码改为：

> define(‘WPLANG’, ‘zh_CN’);

这个时候在刷新页面就成为中文的。

不过，有的英文的wordpress中没有中文语言包，这就需要在多做一点；

下载中文wordpress，将 wordpress/wp-content/ 的 languages 文件夹复制到英文版的对应目录下；

再刷新页面就没有问题了，搞定。

当然这样只是举个例子，要改为其他版本的，则用相同的办法即可。

未经允许不得转载：[空洽网](http://kongqia.com) » [wordpress英文转换为中文](http://kongqia.com/33302.html)


