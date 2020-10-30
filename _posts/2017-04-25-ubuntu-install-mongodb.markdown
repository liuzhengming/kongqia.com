---
layout: post
title: Ubuntu 上安装 MongoDB
date: 2017-04-25 15:58:00.000000000 +08:00
---
运行下列命令，导入 MongoDB 公开 GPG 键：

`sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10`

使用下列命令，创建一个/etc/apt/sources.list.d/mongodb.list 文件。

`echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | sudo tee /etc/apt/sources.list.d/mongodb.list`

运行下列命令，更新存储库：

`sudo apt-get update`

然后利用下列命令安装 MongoDB：

`apt-get install mongodb-10gen=2.2.3`

在上面的命令中，安装的 2.2.3 版本正是 MongoDB 的当前版本。记住一定要及时更新至最新的版本。至此，MongoDB 的安装就成功了。

启动 MongoDB：

`sudo service mongodb start`

停止 MongoDB：

`sudo service mongodb stop`

重启 MongoDB：

`sudo service mongodb restart`

使用 mongodb 时，输入下列命令即可：

`mongo`
