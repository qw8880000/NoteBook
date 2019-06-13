---
title: vim设置配色主题
date: 2017-11-01 17:36:46
categories:
tags:
abbrlink: 207a3e1fac90dec3
---

## 更换配色的方法：
* 找到vim目录，例如我的是`~/.vim`，然后`mkdir ~/.vim/colors`
* 把配色方案放到这下面
* `.vimrc`中加入 `colorscheme  方案名`
```vim
syntax on
syntax enable
set t_Co=256
colorscheme molokai
```

## 我喜欢的配色方案：

* molokai.vim
![image](http://qiniu.wangjinle.com/vim-molokai.png)
* jellybeans.vim
![image](http://qiniu.wangjinle.com/vim-jellybeans.png)
* Tomorrow-Night-Eighties.vim
![image](http://qiniu.wangjinle.com/vim-Tomorrow-Night-Eighties.png)

