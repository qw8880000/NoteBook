---
title: vim安装中文帮助
date: 2017-11-01 17:18:39
categories:
    - vim
tags:
    - vim
abbrlink: 0d1f184e23815ff1
---

# linux 下 安装中文帮助

对于不爱看英文文档的同学，一份中文帮助也许对你有用。

1. 下载vimcdoc安装包
    `wget http://sourceforge.net/projects/vimcdoc/files/vimcdoc/1.8.0/vimcdoc-1.8.0.tar.gz`

2. 解压
    `tar -zxvf vimcdoc-1.8.0.tar.gz`

3. 然后进入 vimcdoc-1.8.0 目录并执行
    `./vimcdoc.sh -i`

NOTE: 使用-i选项的话，缺省同时安装 vimcdoc.vim 全局插件，该插件会在.vim下生成一个plugin目录。
由于我们使用pathgeon来管理插件，而plugin下的插件在pathgeon管理之外。为此可以在安装时跳过 vimcdoc.vim 插件。
可是使用 -I选项来安装： `./vimcdoc.sh -I`

4. 优先使用中文帮助
    `set helplang=cn`

# windows 下安装中文帮助

到[vimdoc](http://vimcdoc.sourceforge.net/) 下直接下载安装程序并安装。

更多内容参考：[vim学习汇总](http://blog.wangjinle.com/posts/9a88772f17a949d5.html)
