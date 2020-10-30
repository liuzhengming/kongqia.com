---
layout: post
title: "@font-face加载字体"
date: 2014-03-05 06:16:26.000000000 +08:00
---

[![bd3eb13533fa828b08d8a91cfc1f4134960a5a51](http://kongqia.com/wp-content/uploads/2014/03/bd3eb13533fa828b08d8a91cfc1f4134960a5a51.jpg)](http://kongqia.com/wp-content/uploads/2014/03/bd3eb13533fa828b08d8a91cfc1f4134960a5a51.jpg)

IE加载外部字体，注意eot格式。

windows store app 也可以使用这个方法加载字体。

css如下：

> @font-face
> 
> {
> 
> font-family: myfont;
> 
> src: url(‘test_font.eot’);
> 
> }

自己需要的字体一般为.ttf，所以需要转换一下；

转换地址：

[http://ttf2eot.sebastiankippe.com](http://ttf2eot.sebastiankippe.com "ttf to eot")

如果还想只是需要字体中的一部分（如只需要字母），就可用字体编辑软件(FontCreator)删除掉多余的内容，会大大减少字体大小；

字体编辑软件 FontCreator 下载地址：

[http://pan.baidu.com/s/1sjpoPkh](http://pan.baidu.com/s/1sjpoPkh "FontCreator")

未经允许不得转载：[空洽网](http://kongqia.com) » [@font-face加载字体](http://kongqia.com/33313.html)


