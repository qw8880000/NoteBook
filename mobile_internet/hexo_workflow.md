---
title: hexo使用grunt实现自动化 | hexo
date: 2017-10-26 22:32:00
categories:
    - hexo
tags:
    - hexo
abbrlink: 3b05183235dcc265
---

开发过前端或者node.js的同学对grunt应该不陌生，如果对grunt不熟悉可略过本文。

开始使用hexo来处理静态博客时我就遇到了问题，我的文章已经写了很多篇了，都是markdown格式，而且托管在github上了，然而hexo并不支持导入文章。
好在我发现只要把markdown文件拷贝到hexo里的`source/_posts`，hexo就会解析，我可以考虑直接把所有文章直接拷贝到这个目录。
但是另外一个问题又出现了，问题在于存在两份一模一样的源文件，一份我托管在github上，一份在`source/_posts`，后期文章改动的话，两边不同步，维护很费力。

后来想到的方法就是利用自动化工具来处理源文件的拷贝，博客的部署等一些操作。由于对grunt比较熟悉，所以使用了grunt。

# 需要的grunt插件

| 插件                | 作用 |
|---------------------|------|
| grunt-bg-shell      |      |
| grunt-contrib-clean |      |
| grunt-contrib-copy  |      |
| grunt-contrib-watch |      |
| grunt-rewrite       |      |
| grunt-shell         |      |
| grunt-zip           |      |
| load-grunt-tasks    |      |


