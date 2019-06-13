---
title: 学会使用vim的help
date: 2017-11-01 17:56:51
categories:
    - vim
tags:
    - vim
abbrlink: 439e8400a2ecdfad
---

你在网络上查找的关于vim的一切问题，vim help都可以回答你，关键是我们会不会搜索help。

# 查看vim帮助

输入：`:help`，显示的是vim帮助的首页，这里列出了help的目录，有很多主题供你进一步查看。
![image](http://qiniu.wangjinle.com/vim-help20171101200032.png)

光标移动到某个主题或者关键字，按下`ctrl-]`，会进入详细内容，按下`ctrl-t`会回到原来位置。

# 查看某关键字的帮助
输入：`:help word`，可以查看匹配此关键字的帮助。

例子：

* 查看有关 折叠 的帮助：`:help fold`
* 查看有关 快捷键 的帮助：`:help map`
* 查看有关 跳转 的帮助：`:help CTRL-O`, `:help CTRL-I`, `:help :jumps`, `:help jump-motions`
* 查看有关 标记 的帮助：`:help mark-motions`

# 使用搜索功能

输入：`helpgrep {pattern}`，搜索所有的帮助文本并给出一个匹配 `{pattern}` 行的列表。跳转到第一个匹配。`{pattern}` 视为 Vim 的正规表达式。

具体如何使用，大家可以使用`:help helpgrep` 去查看详情啦。

