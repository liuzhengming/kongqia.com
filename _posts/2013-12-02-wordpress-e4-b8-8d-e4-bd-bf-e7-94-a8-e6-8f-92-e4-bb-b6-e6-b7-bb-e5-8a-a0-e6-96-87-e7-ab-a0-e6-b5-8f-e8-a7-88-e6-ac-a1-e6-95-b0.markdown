---
layout: post
title: wordpress不使用插件添加文章浏览次数
date: 2013-12-02 03:43:44.000000000 +08:00
---

在functions.php文件，加入以下代码；

> function getPostViews($postID){  
>  $count_key = ‘post_views_count’;  
>  $count = get_post_meta($postID, $count_key, true);  
>  if($count==”){  
>  delete_post_meta($postID, $count_key);  
>  add_post_meta($postID, $count_key, ’0′);  
>  return “0 View”;  
>  }  
>  return $count.’ Views’;  
>  }  
>  function setPostViews($postID) {  
>  $count_key = ‘post_views_count’;  
>  $count = get_post_meta($postID, $count_key, true);  
>  if($count==”){  
>  $count = 0;  
>  delete_post_meta($postID, $count_key);  
>  add_post_meta($postID, $count_key, ’0′);  
>  }else{  
>  $count++;  
>  update_post_meta($postID, $count_key, $count);  
>  }  
>  }

2.  在single.php或index.php或page.php中加入以下代码：

> <?php setPostViews(get_the_ID()); ?> <?php echo getPostViews(get_the_ID()); ?>

好了，现在找篇文章看一下效果吧。

样式就自己调整一下了。

未经允许不得转载：[空洽网](http://kongqia.com) » [wordpress不使用插件添加文章浏览次数](http://kongqia.com/18137.html)


