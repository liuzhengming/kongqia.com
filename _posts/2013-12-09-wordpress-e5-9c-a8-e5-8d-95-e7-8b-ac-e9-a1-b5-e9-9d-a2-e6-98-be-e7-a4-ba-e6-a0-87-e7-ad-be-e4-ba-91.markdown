---
layout: post
title: wordpress在单独页面显示标签云
date: 2013-12-09 06:32:48.000000000 +08:00
---

[![标签云](http://kongqia.com/wp-content/uploads/2013/12/QQ20131208-6@2x-300x283.png)](http://kongqia.com/wp-content/uploads/2013/12/QQ20131208-6@2x.png)

1. 新建文件tags.php

2. 在tags.php中加入以下内容（申明一个Tags模板）：

> <?php  
>  /*  
>  Template Name: Tags  
>  */  
>  ?>

3. 再在tags.php中加入以下内容（获取标签）：

> <?php wp_tag_cloud(‘smallest=14&largest=46&unit=px&number=500′);?>

4. 上传文件至：？wp-content/themes/你使用的模板/

5. 新建页面，标题为：tags

6. 在右侧选择’模板’：tags，如图：

[![选择模板](http://kongqia.com/wp-content/uploads/2013/12/QQ20131208-5@2x-241x300.png)](http://kongqia.com/wp-content/uploads/2013/12/QQ20131208-5@2x.png)

7. 发表文章，打开页面：http://kongqia.com/tags来查看你的成果吧。

 

未经允许不得转载：[空洽网](http://kongqia.com) » [wordpress在单独页面显示标签云](http://kongqia.com/18196.html)


