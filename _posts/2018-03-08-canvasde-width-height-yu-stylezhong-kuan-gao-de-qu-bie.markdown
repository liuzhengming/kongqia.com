---
layout: post
title: canvas的 width、height 与style中宽高的区别
date: 2018-03-08 11:11:14.000000000 +08:00
---
关于HTML5中Canvas的宽、高设置问题
# Canvas元素默认宽 300px, 高 150px, 设置其宽高可以使用如下方法(不会被拉伸)：
### 方法一：
       <canvas width="500" height="500"></canvas>
### 方法二：使用HTML5 Canvas API操作 OK
       var canvas = document.getElementById('欲操作canvas的id');
       canvas.width = 500;
       canvas.width = 500;
# 若通过如下方法设置宽高，那么Canvas元素将由原来大小被拉伸到所设置的宽高：
### 方法一：使用CSS 会被拉伸
     #欲操作canvas的id｛
          width:1000px;
          height:1000px;
     ｝
### 方法二：使用HTML5 Canvas API操作 会被拉伸
      var canvas = document.getElementById('欲操作canvas的id');
      canvas.style.width = "1000px";
      canvas.style.height = "1000px";
### 方法三 ：用jquery的$("#id").width(500);会被拉伸
# 其它：canvas的width和height也不能用百分比表示。canvas会将百分值当成数值显示
