---
title: 生成永久链接 | hexo
date: 2017-10-18 22:31:52
categories:
    - hexo
tags:
    - hexo 
abbrlink: @@abbrlink
---

hexo默认的文章链接形式为`domain/year/month/day/postname`，当我们把文章源文件名改掉之后，链接也会改变，这很不友好。
这里介绍一种方法来生成永久链接。使用的是node.js常用的自动构建工具Grunt.
