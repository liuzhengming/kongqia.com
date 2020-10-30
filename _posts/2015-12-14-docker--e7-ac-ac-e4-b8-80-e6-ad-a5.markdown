---
layout: post
title: docker 第一步
date: 2015-12-14 19:14:10.000000000 +08:00
---

1、  
 mkdir -p /opt/gitlab/data /opt/gitlab/log  
 2、  
 docker run \  
 –name=’gitlab’ \  
 -itd \  
 -e ‘GITLAB_PORT=10080′ \  
 -e ‘GITLAB_SSH_PORT=10022′ \  
 -p 10022:22 -p 10080:80 \  
 -p 127.0.0.1:10080:10080/udp \  
 -v /var/run/docker.sock:/run/docker.sock \  
 -v $(which docker):/bin/docker \  
 -v /opt/gitlab/data:/home/git/data \  
 -v /opt/gitlab/log:/var/log/gitlab \  
 gitlab/gitlab-ce

未经允许不得转载：[空洽网](http://kongqia.com) » [docker 第一步](http://kongqia.com/33662.html)


