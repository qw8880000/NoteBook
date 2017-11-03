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

## gvim的vundle 安装插件出错

错误提示如下：
```sh
Processing 'gmarik/vundle'
Error detected while processing function vundle#installer#new..<SNR>129_process..vundle#installer#run..vundle#installer#install..<SNR>129_sync..<SNR>129_system:
line    1:
E484: Can't open file C:\Users\gallia1\AppData\Local\Temp\VIo8E1E.tmp
Error detected while processing function vundle#installer#new..<SNR>129_process:
line   13:
E121: Undefined variable: g:vundle_last_status
E15: Invalid expression: 'error' == g:vundle_last_status
line   17:
E121: Undefined variable: g:vundle_last_status
E15: Invalid expression: 'updated' == g:vundle_last_status && empty(msg)
```

解决方法：
1. 把vim74(如：`C:\Program Files\gVimPortable\vim74`)加入系统变量Path
2. 安装 git for Windows ,选择`Run git from Windows command prompt option`

参考：[Vundle for Windows](https://github.com/VundleVim/Vundle.vim/wiki/Vundle-for-Windows)

