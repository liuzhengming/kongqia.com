---
layout: post
title: 自定义二级域名作为WordPress图片附件地址
date: 2013-11-21 04:45:06.000000000 +08:00
---

方法比较简单，努力看完哦。

1. 登入你域名的管理后台，添加二级域名 pic 的解析。
2. 登入你空间的管理后台，添加二级域名 pic 对空间目录访问。
3. 登入自己WordPress后台，打开 设置 – 媒体 的控制选项，在默认上传路径处填写放置图片文件夹的目录，这里目录都是相对根目录的。我的就填写dl/pic。在文件的完整URL地址填写你要访问图片附件的地址，如http://pic.kongqia.com/pic

这样做完后，以前的图片链接都会出现错误，在登入你的数据库管理，在你WordPress数据库中运行

<div>> <div id="highlighter_830736">`UPDATE``wp_posts`<div>`SET``post_content = ``REPLACE``(post_content, ``'<a href="http://www./">http://www.</a>旧网址.com'``, ``'<a href="http://www./">http://www.</a>新网址.com'``)`</div></div>

</div>确保以前的图片地址更改为现在的。

另外在媒体选项中还有个以 年—月 这样目录形式上传进行图片保存的选项，假如你想的话，要在选中前面的小框框的哦。否则是会以attachment_id=xx的方式访问。

未经允许不得转载：[空洽网](http://kongqia.com) » [自定义二级域名作为WordPress图片附件地址](http://kongqia.com/18037.html)


