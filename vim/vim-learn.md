@Author:         wangjl  
@Date:           2016-09-22 22:31  
@Description:    

# 查看vim帮助

输入： `:help`

看到关键字，使用以下快捷键可以跳转到对应章节： `ctrl + ]`

# 分割窗口

水平分割： `:vsplit`

垂直分割： `:vertical`

# 配色方案

更换配色的方法：
```
    1. mkdir ~/.vim/colors
    1. 把配色方案放到这下面
    1. .vimrc中加入 colorscheme  方案名

        syntax on
        syntax enable
        set t_Co=256
        colorscheme molokai
```

我喜欢的配色方案：

* molokai.vim
* jellybeans.vim
* Tomorrow-Night-Eighties.vim


[挑選 Vim 顏色(Color Scheme)](http://blog.longwin.com.tw/2009/03/choose-vim-color-scheme-2009/)
    
# 安装vundle插件

```shell
    mkdir ~/.vim
    git clone https://github.com/gmarik/vundle.git ~/.vim/bundle/vundle
```

安装完vundle插件后，就可以用来管理其他插件了

# 安装中文帮助

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


# 折叠

查看帮助：`:h fold`

# 快捷键

查看帮助：`:h map` , `:h noremap`

* 查看所有快捷键映射：`:map`
* 查看normal模式下快捷键：`:nmap`
* 查看insert模式下快捷键：`:imap`
* 查看某快捷键映射：`:verbose map <所要查找的快捷键>` 


# 跳转

查看帮助： `:help CTRL-O`, `:help CTRL-I`, `:help :jumps`, `:help jump-motions`

# 标记

`:help mark-motions`

# 获取当前光标下单词

`<C-R><C-W>`

# 常用按键的表示

```
    <Esc>代表Escape键:
    <CR>代表Enter键；
    <D>代表Command键。
    Alt键可以使用<M-key>或<A-key>来表示。
    <C>代表Ctrl.
    组合键，可以用<C-Esc>代表Ctrl-Esc；使用<S-F1>表示Shift-F1
```

# Vim命令理解

这部分来源 [一起来说 Vim 语](http://www.jianshu.com/p/a361ce8c97bc)，理解此部分是需要你已经了解了 Vim 的几种常用的工作模式（正常模式、插入模式、命令模式等）

### 动词

动词代表了我们打算对文本进行什么样的操作。例如：

```bash
d # 表示删除delete
r # 表示替换replace
c # 表示修改change
y # 表示复制yank
v # 表示选取visual select
```

### 名词

名词代表了我们即将处理的文本。Vim 中有一个专门的术语叫做 [文本对象] text object，下面是一些文本对象的示例：

```bash
w # 表示一个单词word
s # 表示一个句子sentence
p # 表示一个段落paragraph
t # 表示一个 HTML 标签tag
引号或者各种括号所包含的文本称作一个文本块。
```

### 介词

介词界定了待编辑文本的范围或者位置。

```bash
i # 表示在...之内 inside
a # 表示环绕... around
t # 表示到...位置前 to
f # 表示到...位置上 forward
```

### 数词

数词指定了待编辑文本对象的数量，从这个角度而言，数词也可以看作是一种介词。引入数词之后，文本编辑命令的语法就升级成了下面这样：

```
动词 介词/数词 名词
```

下面是几个例子：

```bash
c3w  # 修改三个单词：change three words
d2w  # 删除两个单词：delete two words
```

另外，数词也可以修饰动词，表示将操作执行 n 次。于是，我们又有了下面的语法：

```
数词 动词 名词
```

请看示例：

```bash
2dw # 两次删除单词（等价于删除两个单词）: twice delete word
3x  # 三次删除字符（等价于删除三个字符）：three times delete character
```

### 组词为句

有了这些基本的语言元素，我们就可以着手构造一些简单的命令了。文本编辑命令的基本语法如下：

```
动词 介词 名词
```

下面是一些例子（如果熟悉了上面的概念，你将会看到这些例子非常容易理解），请亲自在 Vim 中试验一番。

```bash
dip # 删除一个段落: delete inside paragraph
vis # 选取一个句子: visual select inside sentence
ciw # 修改一个单词: change inside word
caw # 修改一个单词: change around word
dtx # 删除文本直到字符“x”（不包括字符“x”）: delete to x
dfx # 删除文本直到字符“x”（包括字符“x”）: delete forward x
```

# vimscript - vim编程语言

查看帮助：`:help vim-script-intro`


# 参考 

* [vim 配置 example](https://github.com/VundleVim/Vundle.vim/wiki/Examples)
* [ 到底 VIM 能配置到多强大的程度？ ](https://www.zhihu.com/question/20151659)
