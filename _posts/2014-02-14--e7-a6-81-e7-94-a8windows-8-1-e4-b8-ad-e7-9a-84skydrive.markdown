---
layout: post
title: 禁用Windows 8.1中的SkyDrive
date: 2014-02-14 04:58:25.000000000 +08:00
---

[![148148291](http://kongqia.com/wp-content/uploads/2014/02/148148291.jpg)](http://kongqia.com/wp-content/uploads/2014/02/148148291.jpg)

微软在windows 8.1中整合了skydrive，skydrive应用、资源管理器中的skydrive。但是我现在用不到云服务，所以要关闭这个skydrive。方法如下：

**通过本地组策略来禁用skydrive**

1. 在运行窗口中输入gpedit.msc

[![20131107112448457](http://kongqia.com/wp-content/uploads/2014/02/20131107112448457.jpg)](http://kongqia.com/wp-content/uploads/2014/02/20131107112448457.jpg)

 

2. 打开本地组策略编辑器

[![20131107112449602](http://kongqia.com/wp-content/uploads/2014/02/20131107112449602.jpg)](http://kongqia.com/wp-content/uploads/2014/02/20131107112449602.jpg)

 

3. 打开本地计算机策略>计算机配置>管理模板>Windows组件>SkyDrive，可看到阻止使用SkyDrive执行文件存储选项，双击打开该选项

[![20131107112449539](http://kongqia.com/wp-content/uploads/2014/02/20131107112449539.jpg)](http://kongqia.com/wp-content/uploads/2014/02/20131107112449539.jpg)

4. 将未配置修改为已启用，完成后将可禁用skydrive。如需还原只需将已启用修改为未配置或是已禁用，然后重启资源管理器即可。

未经允许不得转载：[空洽网](http://kongqia.com) » [禁用Windows 8.1中的SkyDrive](http://kongqia.com/33278.html)


