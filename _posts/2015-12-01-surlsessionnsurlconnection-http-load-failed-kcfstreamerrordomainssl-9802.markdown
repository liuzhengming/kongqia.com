---
layout: post
title: SURLSession/NSURLConnection HTTP load failed (kCFStreamErrorDomainSSL, -9802)
date: 2015-12-01 22:02:32.000000000 +08:00
---

错误：NSURLSession/NSURLConnection HTTP load failed (kCFStreamErrorDomainSSL, -9802)

原因：在 iOS9中,在网络通话中ATS强制采用最佳实践,包括使用HTTPS.

改正：右击Info.plist 文件 -> Open As > Source Code  
 然后添加下面代码在最后的`</dict>`之前:

> <key>NSAppTransportSecurity</key>  
>  <dict>  
>  <key>NSAllowsArbitraryLoads</key>  
>  <true/>  
>  </dict>

OK。

未经允许不得转载：[空洽网](http://kongqia.com) » [SURLSession/NSURLConnection HTTP load failed (kCFStreamErrorDomainSSL, -9802)](http://kongqia.com/33658.html)


