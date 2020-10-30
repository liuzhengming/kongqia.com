---
layout: post
title: win10+java8+ie11环境下运行applet
date: 2016-04-16 00:49:59.000000000 +08:00
---

在win10+java8+ie11环境下，要支持applet，需进行以下操作：  
 1.在IE的Internet选项->安全->Internet->自定义级别中，  
 A）对ActiveX控件和插件下项进行如下操作：  
 （1）ActiveX控件自动提示 启用  
 （2）对标记为可安全执行脚本的ActiveX控件之星脚本 启用  
 （3）对未标记为可安全执行脚本的ActiveX控件初始化并执行脚本 提示  
 （4）二进制文件和脚本行为 启用  
 （5）仅允许经过批准的域在未经提示的情况下使用ActiveX 启用  
 （6）下载未签名的ActiveX控件 提示  
 （7）下载已签名的ActiveX控件 提示  
 （8）允许ActiveX筛选 启用  
 （9）允许Scriptlet 提示  
 （10）允许运行以前未使用的ActiveX控件而不提示 禁用  
 （11）运行ActiveX控件和插件 启用  
 （12）在ActiveX控件上运行反恶意软件 启用  
 （13）在没有使用外部媒体播放机的网页上显示视频和动画  
 B）对脚本下的java小程序脚本设置为启用  
 2.安装jdk8，设置JAVA_HOME和CLASSPATH  
 3.安装java8（版本和jdk版本需对应），在控制面板中，右上角查看方式，选择小图标，然后选择java->安全。  
 由于java8安全级别只有很高和高，因此要访问自己的程序，需设置例外站点。  
 点击编辑站点列表->添加，添加站点URL。例外站点支持https和file，这里文件存在本地，因此选file，设置为file:///D:/eclipseProject/javaStudy/bin/graphics/（注意最后的“/”），点击确定完成。  
 4.写applet程序和相应html的方法有很多资料，这里不再赘述。

未经允许不得转载：[空洽网](http://kongqia.com) » [win10+java8+ie11环境下运行applet](http://kongqia.com/33699.html)


