---
title: vim基础教程 | 20分钟学会vim
date: 2017-11-01 17:15:36
categories:
    - vim
tags:
    - vim
abbrlink: 9304e83ce54e7fdf
---

stackoverflow 在vim类的问题里，有超过100万次提问是关于，如何退出vim，哈哈。
要高效的使用vim，学习曲线实在是太陡了，所以我的真实建议是换IDE，除非你热爱vim，但是一些简单的操作还是可以学习一下，也能用。

学习vim第一步，当然是如何退出vim，然后是移动、增删改查、保存，后面如果还有兴趣就学习一些进阶操作。

# 学会退出vim

先按`esc`，再依次按下`:q!`，最后按回车

# 预备知识

常见的vim有三种模式：
* normal mode(普通模式)
* insert mode(插入模式)
* command-line mode(命令行模式)

**打开vim时默认是处理普通模式**。
**按下`esc`将从其他模式返回到普通模式**。

# 如何移动

首先进入到普通模式，然后使用`hjkl`进行移动。
h,j,k,l 分别表示 左，下，上，右.

```
  k        上
h   l    左  右
  j        下
```
hjkl代表的方向很难记？试试口决`j下k上`，而hl在两边自然代表左右，记忆量变少，可能会好记很多。

# 如何输入

按下`i`，将进入插入模式，然后就可以输入字符啦，当然按下`back`键可以删除字符。

如果想移动，按下`esc`返回普通模式再移动。

# 如何保存修改

首先进入到普通模式，然后按下`:w`

# 更多

* [vim学习汇总](http://blog.wangjinle.com/posts/9a88772f17a949d5.html)
* [学会使用vim的help](http://blog.wangjinle.com/posts/439e8400a2ecdfad.html)
* [pratical VIM](http://oxnimkw03.bkt.clouddn.com/Practical Vim.pdf)
* [learn vimscript the hard way](http://learnvimscriptthehardway.onefloweroneworld.com/)
