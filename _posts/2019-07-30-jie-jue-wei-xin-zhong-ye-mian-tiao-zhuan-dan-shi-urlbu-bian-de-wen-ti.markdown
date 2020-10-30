---
layout: post
title: 解决vue在微信中页面跳转，但是url不变的问题
date: 2019-07-30 18:06:14.000000000 +08:00
---
### 问题描述

vue在微信浏览器中做`$router.push` `$router.replace`等操作，页面可以正常跳转显示，但是通过复制链接或浏览器打开，都显示为初次进来的链接。

### 原因

微信对history的操作支持不太友好

### 解决办法

在公共路由守护中做处理，代码如下：

```javascript
this.$router.afterEach((to) => {
    window.setTimeout( _ => {
        window.location = window.location // 这一段是核心代码
        console.log('window.location')
    }, 500)
})
```
