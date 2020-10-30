---
layout: post
title: wordpress二级域名多站点设置
date: 2013-11-16 17:17:01.000000000 +08:00
---

WordPress 3.0已经发布有差不多半个月了，WP3.0有个对我们来说比较实用 的功能，就是他的多站点模式。WordPress 3.0的多站点模式既可以是二级域名的形式，也可以通过目录的方式来实现。今天刚刚拿个域名捣鼓了一下子设置问题，在这里分享一下如何激活 WordPress 3.0二级域名多站点模式和其中的一些配置问题。

![](http://www.admin5.com/upimg/allimg/100707/1422220.jpg) 

WordPress 3.0多站点功能

首先，WordPress 3.0里的多站点模式默认情况下是没有开启的，需要先激活。激活很简单，打开根目录下的wp-config.php(请记得备份)，找到这么一行

/* That’s all, stop editing! Happy blogging. */:

在这行的上面添加这段代码：

define(‘WP_ALLOW_MULTISITE’, true);

这样你的network就被激活了，在Tools栏下也会多一个network的选项。

![](http://www.admin5.com/upimg/allimg/100707/1422221.jpg) 

点此Network选项后，将被引导到Network创建页面

![](http://www.admin5.com/upimg/allimg/100707/1422222.jpg) 

　　WordPress 3.0多站点网络创建

　　我这里是已经创建好了的界面，可能跟创建前有点不太一样。大家可以按他的提示进行配置修改文 件。(需要修改到wp-config.php和.htaccess这两个文件)

注意：二级域 名的多站点WordPress需要泛域名的支持。泛域名的设置很简单，在dns设置中添加一条*记录即可。

*.example.com. IN A 192.168.1.1

好了，一切设置完成提交创建后，会提示要你重新登录。这时再用管理员账号重新登录后，就会发 现在以往的Dashboard之上多了个Super Admin的面板。

![](http://www.admin5.com/upimg/allimg/100707/1422223.jpg) 

Super Admin控制面板

在这里，就可以进行各种配置，添加删除网站/用户这些操作了，具体大家自己玩会就清晰了。 WordPress 3.0的多站点模式可以让我们更方便的进行博客链接工厂的 操作，所以在这里我写了这个激活设置教程，大家如果有什么问题的，请留言一起讨论吧。

原创文章，转载请注明： 转载自http://semthinking.com/blackhat/276

未经允许不得转载：[空洽网](http://kongqia.com) » [wordpress二级域名多站点设置](http://kongqia.com/17970.html)


