---
title: 使用vim遇到过的问题
date: 2017-11-01 18:04:03
categories:
    - vim
tags:
    - vim
abbrlink: ea6564634f9891e5
---

## 在Vim中鼠标右键不能粘贴

[【转载】解决在Vim中鼠标右键不能粘贴](http://www.cnblogs.com/centimeter/archive/2012/03/14/2395427.html)

## vim 编辑的中文注释在source insight下乱码

原因：source insight 不支持utf-8编码，支持的是cp936
解决：使用`iconv`来转换编码，例如`iconv -f utf-8 -t cp936 file1.txt -o file1.txt`

## 为什么 VIM 编辑变慢

有可能是因为输入的字符与快捷键冲突

