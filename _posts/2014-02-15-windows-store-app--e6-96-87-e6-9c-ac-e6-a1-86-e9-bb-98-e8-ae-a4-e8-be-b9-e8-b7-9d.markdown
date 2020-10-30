---
layout: post
title: windows store app 文本框默认边距
date: 2014-02-15 18:23:50.000000000 +08:00
---

[![307021517305](http://kongqia.com/wp-content/uploads/2014/02/307021517305.jpg)](http://kongqia.com/wp-content/uploads/2014/02/307021517305.jpg)

 

最近开发windows store app的时候发现input总有内边距，这个问题给了我许多的困惑；

之前没有遇到过这样的问题，但是有点想法，就是引用了ui-dark.css，愿意肯定就是这个；

开始一行一行看ui-dark.css，当看到231行的时候，出现了这样的样式：

> input::-ms-value {
> 
> margin: 4px 8px;
> 
> }

瞬间豁然开朗，问题找到了，只要恢复margin为0就好了，解决如下：

> input::-ms-value {
> 
> margin: 0;
> 
> }

未经允许不得转载：[空洽网](http://kongqia.com) » [windows store app 文本框默认边距](http://kongqia.com/33284.html)


