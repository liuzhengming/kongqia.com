---
layout: post
title: Ubuntu install Swift
date: 2017-03-30 10:55:43.000000000 +08:00
---
Swift的开发环境可以使用苹果平台（OS X）或Linux系统（Ubuntu），这里介绍在我在Ubuntu 14 server下安装Swift运行环境的过程
### 安装所需的依赖项
```
sudo apt-get install clang  
sudo apt-get install clang libicu-dev  
```
### 下载最新的二进制版本（swift.org）
```
wget https://swift.org/builds/swift-2.2-release/ubuntu1404/swift-2.2-RELEASE/swift-2.2-RELEASE-ubuntu14.04.tar.gz  
```
### 导入PGP密钥到你的钥匙圈
```
wget -q -O - https://swift.org/keys/all-keys.asc | gpg --import -  
```
### 验证PGP签名（可选）
```
gpg --keyserver hkp://pool.sks-keyservers.net --refresh-keys Swift 
```
### 解压文件
```
tar xzf swift-2.2-RELEASE-ubuntu14.04.tar.gz 
```
### 添加Swift到你的Path环境变量
```
vim ~/.bashrc添加export PATH=/home/aven/swift-2.2-RELEASE-ubuntu14.04/usr/bin:"${PATH}"  至最后一行
```
`转至http://blog.csdn.net/testcs_dn/article/details/51056949`
