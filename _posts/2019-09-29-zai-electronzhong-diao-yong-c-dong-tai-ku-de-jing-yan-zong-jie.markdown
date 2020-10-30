---
layout: post
title: 在electron中调用C++动态库的经验总结
date: 2019-09-29 16:08:36.000000000 +08:00
---
具体查看链接：

https://blog.csdn.net/wang839305939/article/details/83780789

https://blog.csdn.net/lhangtk/article/details/82984148


关键：

node-gyp rebuild --arch=ia32 --dist-url=https://atom.io/download/atom-shell --runtime=electron --target=3.0.3



