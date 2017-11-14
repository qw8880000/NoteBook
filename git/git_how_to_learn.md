---
title: 我是如何学习git
date: 2017-11-08 18:04:02
categories:
  - git
tags:
  - git
abbrlink: 808409bee5ab8c2a
---

一开始学习git的时候，网上的git教程很多，看得人眼花缭乱，不知道如何下手。现在对git已经很熟悉了，回过头来总结一下学习方法。

一般官方文档是最全面，但是不一定适合快速上手。我们可以学习一些快速上手的教程，这些教程没有官方文档那么全面，但是可以学习到最常用的操作，适合入门。

入门之后，如果还想进阶，那就建议撸一遍官方教程。

# 入门

入门教程推荐：
* [廖雪峰的git教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
* [git教程-易百](http://www.yiibai.com/git/)

# 进阶

上面的入门教程只能让你会用，如果想要了解git的原理和一些进阶的操作，那么还是要看比较全面权威的文档。

这里推荐被称为git圣经的《pro git》，我在写本文时已经发布到v2版本了，以下是链接：[《pro git》- v2](https://git-scm.com/book/zh/v2)。

一开始学习git的时候我去看《pro git》，当时觉得很多概念很难理解。后来用了一段时间的git，对git有了一些基础概念后，再回过头来看《pro git》，感觉理解上简单了很多。

# 技能树

学习完《pro git》，可以得到一个git技能树：
![image](http://oxnimkw03.bkt.clouddn.com/git_tech_tree_v2.png)

# 学会使用帮助

git的命令太多了，有时候一些参数很容易忘记。我以前的做法是到网上去搜索对应的命令用法，后来发现可以使用git的帮助直接查询，节省了很多时间。

使用 Git 时需要获取帮助，有三种方法可以找到 Git 命令的使用手册：
```sh
$ git help <verb>
$ git <verb> --help
$ man git-<verb>
```

例如，要想获得 config 命令的手册，执行:
```sh
$ git help config
```

# 更多

* [git 学习汇总](http://blog.wangjinle.com/posts/fd56adc47e2516b6.html)
* git游戏:[Learn Git Branching](http://pcottle.github.io/learnGitBranching/)。

