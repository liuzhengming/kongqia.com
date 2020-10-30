---
layout: post
title: zeromq c++ java配置
date: 2016-06-13 19:15:39.000000000 +08:00
---

1.C++  
 1）下载zeromq4.0.4.exe并安装；  
 2）下载cppzmq-master.zip解压，其中包含zmq.hpp和zmq_addon.hpp两个头文件；  
 3）新建vs2010项目及cpp文件，选择项目->属性->C++->常规->附加库目录，将zeromq4.0.4安装目录下的include路径，及cpp-master.zip解压后的文件夹路径，添加到此处；  
 4）选择项目->属性->链接器->常规->附加库目录，将zeromq4.0.4安装目录下的lib路径添加到此处；  
 5）选择项目->属性->链接器->输入->附加依赖项，将4）中对应的lib名称和后缀添加到此处；  
 6）完成。  
 2.java  
 官网没有现成的java安装包，需要下载源码，编译生成java的jar包。此处感谢网友放上去的编译好的包，省去了编译的流程。

未经允许不得转载：[空洽网](http://kongqia.com) » [zeromq c++ java配置](http://kongqia.com/33709.html)


