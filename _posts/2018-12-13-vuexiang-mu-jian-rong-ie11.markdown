---
layout: post
title: vue项目兼容IE11
date: 2018-12-13 10:48:01.000000000 +08:00
---
1、npm安装babel-polyfill

`npm install babel-polyfill --save-dev`

2、在入口文件main.js中引入
`import 'babel-polyfill'`
