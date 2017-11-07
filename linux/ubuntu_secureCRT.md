---
title: secureCRT连接ubuntu慢
date: 2017-11-07 21:59:08
categories:
  - linux
tags:
  - linux
abbrlink: @@abbrlink
---

可能原因为：DNS的解析IP导致.

解决办法：

1. 在ssh服务端上更改/etc/ssh/sshd_config 文件中的配置增加：`UseDNS no`
1. 重启ssh服务: /etc/init.d/ssh restart

