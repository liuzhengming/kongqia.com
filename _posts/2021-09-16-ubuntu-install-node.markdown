---
layout: post
title: ubuntu install node
date: 2021-09-16 18:22:40.000000000 +08:00
---

### 安装过程

更新软件源

`sudo apt update`

安装 npm

`sudo apt install npm`

安装 n 模块

注：n 模块是用来安装各种版本的 node 的一个工具。参数 -g 表示全局安装

`sudo npm install n -g`

安装最新长期支持版 node

`sudo n lts`

检验

`node -v`
