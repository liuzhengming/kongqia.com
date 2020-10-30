---
layout: post
title: Wordpress Cannot redeclare comment_mail_notify()解决办法
date: 2013-12-30 04:19:41.000000000 +08:00
---

今天，想找几个主题换个心情，就在百度google了一会，

之后在切换某主题时出现以下错误：

> Cannot redeclare comment_mail_notify()
> 
> Cannot redeclare _check_isactive_widget()

整个人蒙了，又找了关于整个问题的原因，但是都只说了以下简单的处理的办法；

最终，看到一个文章《[检测到几款主题存在恶意广告代码](http://kongqia.com/31917.html)》，才知道网站被植入恶意代码了。

这时候就需要有个解决办法：

1. 在官网下载一个原版的wordpress，拷贝某个主题下function.php文件。

2. 通过FTP覆盖当前主题下的function.php文件。

3. 这个时候你在访问就会发现网站可以用了。

未经允许不得转载：[空洽网](http://kongqia.com) » [WordPress Cannot redeclare comment_mail_notify()解决办法](http://kongqia.com/31916.html)


