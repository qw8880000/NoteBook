---
title: git 不常用操作
date: 2017-11-14 10:41:04
categories:
  - git
tags:
  - git
abbrlink: 17ec4c6ceea10eeb
---

# 把其他分支的某个提交合并到当前分支

```sh
    git cherry-pick <commit id>
```

# 部分克隆

```sh
git clone --depth=14 https://github.com/angular/angular-phonecat.git
```

# log书写规范

第一行为标题，然后换行，写入详细内容，例如：
```
这是一个新功能:
* 如何实现
* 满足什么需求
* 功能如何使用
* 等等
```

# 改变origin 的 url

原先克隆的一个仓库，使用的是http协议的地址克隆的。http协议在push的时候需要使用用户名与密码验证，比较烦人，于是想把仓库的远端git地址改为ssh协议或者git协议，这样就可以使用密钥验证，无需手动验证。

使用命令： ` git remote set-url <name> <url> `。例如：`git remote set-url origin git@github.com:qw8880000/neosnippet-snippets.git`


# 更多

* [git 学习汇总](http://blog.wangjinle.com/posts/fd56adc47e2516b6.html)
