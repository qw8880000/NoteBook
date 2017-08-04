## Introduction

用来放一些vim遇到的问题或其他不好归类的知识。


## 获取当前光标下单词

```
1. <C-R><C-W>
2. <C-R>=expand("<cword>")
```

## 遇到的问题

> map <Leader>p :!start "C:\Program Files\Google\Chrome\Application\chrome.exe" "%:p"<CR> 

    现象：  
    
    执行<Leader>p 后，本应该是调用了chrome 打开了当前文件。
    问题是路径或文件名带中文时，中文传给chrome后乱码了；如果是全英文就能正常实现功能。
    
    原因：  
    
    * gvim 的 encoding 为 utf-8 ，这种情况下它是把中文字符按utf-8的格式发给 chrome。
    * 传给chrome 的路径 应该要使用的是cp936编码格式的

    解决：

## vim 配色

* solarized
* molokai

    [挑選 Vim 顏色(Color Scheme)](http://blog.longwin.com.tw/2009/03/choose-vim-color-scheme-2009/)

## 查看vim打开时的加载时间
```
vim --startuptime timefile the_file_you_want_to_edit
```

## 查看快捷键映射

查看所有                :map
查看normal模式下快捷键  :nmap
查看insert模式下快捷键  :imap

查看某快捷键映射：
    :verbose map <所要查找的快捷键> 

## 常用按键的表示

文／MidSummer（简书作者）
原文链接：http://www.jianshu.com/p/2c9a85277d49
著作权归作者所有，转载请联系作者获得授权，并标注“简书作者”。

    <Esc>代表Escape键:<CR>代表Enter键；<D>代表Command键。
    Alt键可以使用<M-key>或<A-key>来表示。<C>代表Ctrl.
    对于组合键，可以用<C-Esc>代表Ctrl-Esc；使用<S-F1>表示Shift-F1

## 为什么 VIM 编辑变慢

有可能是因为输入的字符与快捷键冲突

## vim 格式化代码

使用这4个键，格式化全部：
    gg=G

    gg  —— 到达文件最开始 
    =   —— 要求缩进 
    G   —— 直到文件尾 

格式化部分：

    按住Shift+v，即大写V，进入可视化编辑的列编辑模式
    选中代码
    按下等号=，格式化所有代码
    
## 查看vim使用的插件

    :scriptnames
## 查看文件全路径

按1 然后 ctrl + g

## vim 覆盖模式

shift + r

## 解决在Vim中鼠标右键不能粘贴

[【转载】解决在Vim中鼠标右键不能粘贴](http://www.cnblogs.com/centimeter/archive/2012/03/14/2395427.html)

## vim 编辑的中文注释在source insight下乱码

原因：source insight 不支持utf-8编码
解决：iconv -f utf-8 -t  cp936 file1.txt -o file2.txt     
       将utf-8编码的file1.txt文件转换成cp936编码的file2.txt文件

## vim 技巧之重复

-   [Vim技巧之重复](http://blog.csdn.net/ii1245712564/article/details/46496347)

## vim 视频教程

-   [Learn Essential Vim Skills](http://vimcasts.org/episodes/)


## 参考资料

[Vim及VimScript资料总结](http://blog.csdn.net/fudesign2008/article/details/7087544)
[VimScript](http://learnvimscriptthehardway.stevelosh.com/)
[Git时代的VIM不完全使用教程](http://beiyuu.com/git-vim-tutorial/)
[Best of Vim Tips](http://www.rayninfo.co.uk/vimtips.html)

[use vim as ide ](https://github.com/yangyangwithgnu/use_vim_as_ide)

## vim 游戏 

http://vim-adventures.com/
