---
title: vim的一些操作
date: 2017-11-01 17:59:09
categories:
    - vim
tags:
    - vim
abbrlink: f050a46bc0f94f8c
---

# 分割窗口

水平分割： `:vsplit`
垂直分割： `:vertical`

# 查看快捷键

查看帮助：`:h map` , `:h noremap`

* 查看所有快捷键映射：`:map`
* 查看normal模式下快捷键：`:nmap`
* 查看insert模式下快捷键：`:imap`
* 查看某快捷键映射：`:verbose map <所要查找的快捷键>` 

# 常用按键的表示

* `<Esc>`代表`Escape`键:
* `<CR>`代表`Enter`键；
* `<D>`代表`Command`键。
* `Alt`键可以使用`<M-key>`或`<A-key>`来表示。
* `<C>`代表`Ctrl`.
* 组合键，可以用`<C-Esc>`代表`Ctrl-Esc`；使用`<S-F1>`表示`Shift-F1`

# 获取当前光标下单词

`<C-R><C-W>`

# vimscript - vim编程语言

查看帮助：`:help vim-script-intro`

# 查看vimrc路径

`:echo $MYVIMRC`

# 查看vim打开时的加载时间

`vim --startuptime timefile the_file_you_want_to_edit`


# vim 格式化代码

使用这4个键，格式化全部：`gg=G` 
解释：
* `gg`: 到达文件最开始 
* `=`: 要求缩进
* `G`: 直到文件尾 

格式化部分：
* 选中代码
* 按下等号`=`，进行缩进调整

# 查看vim使用的插件

`:scriptnames`

# 查看文件全路径

按`1` 然后 `ctrl + g`


