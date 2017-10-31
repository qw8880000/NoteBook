---
title: linux下安装vim
date: 2017-10-31 09:13:18
categories:
    - vim
tags:
    - vim
abbrlink: 05b923573fb51f7a
---

linux下安装vim常见的步骤。

# 删除旧版本vim
```shell
    sudo apt-get remove vim  
    sudo apt-get remove vim-runtime  
    sudo apt-get remove gvim  
    sudo apt-get remove vim-tiny  
    sudo apt-get remove vim-common  
    sudo apt-get remove vim-gui-common 
```
# 下载源码

-   [vim-7.4.tar.bz2](ftp://ftp.vim.org/pub/vim/unix/vim-7.4.tar.bz2)

# 编译前的配置

解压源码，进入对应目录，执行以下配置。
```shell
    ./configure \
    --with-features=huge \
    --enable-pythoninterp --enable-perlinterp \
    --enable-rubyinterp --enable-luainterp \
    --enable-multibyte --enable-fontset \
    --with-features=huge \
    --enable-pythoninterp \
    --enable-perlinterp \
    --enable-rubyinterp \
    --enable-luainterp \
    --enable-multibyte \
    --enable-sniff \
    --enable-gui=gtk2 \
    --enable-cscope
```

其中参数说明如下：

* --prefix=/usr/local/vim74:编译安装路径
* --with-features=huge：支持最大特性
* --enable-pythoninterp：启用Vim对python编写的插件的支持
* --enable-perlinterp：启用Vim对perl编写的插件的支持
* --enable-rubyinterp：启用Vim对ruby编写的插件的支持
* --enable-luainterp：启用Vim对lua编写的插件的支持
* --enable-multibyte：多字节支持 可以在Vim中输入中文
* --enable-sniff：Vim状态提示 提示Vim当前处于INSERT、NORMAL、VISUAL哪种模式
* --enable-cscope：Vim对cscope支持
* --enable-gui=gtk2：gtk2支持,也可以使用gnome，表示生成gvim

# 编译安装

```shell
    make 
    sudo make install
```

# 确认是否安装成功

终端下输入 vim ，如果无错误信息即可

# 把vim作为默认编辑器

```
    sudo update-alternatives --install /usr/bin/editor editor /usr/bin/vim 1 
    sudo update-alternatives --set editor /usr/bin/vim
    sudo update-alternatives --install /usr/bin/vi vi /usr/bin/vim 1 
    sudo update-alternatives --set vi /usr/bin/vim
```

# 更换配色方案

方法：

1. `mkdir ~/.vim/colors`
1. 把配色方案放到这下面
1. `.vimrc`中加入 colorscheme  方案名
```
syntax on
syntax enable
set t_Co=256
colorscheme molokai
```

我喜欢的配色方案：

* molokai.vim
* jellybeans.vim
* Tomorrow-Night-Eighties.vim
    
# 安装vundle插件
```
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

NOTE: 使用`-i`选项的话，缺省同时安装 vimcdoc.vim 全局插件，该插件会在.vim下生成一个plugin目录。
由于我们使用pathgeon来管理插件，而plugin下的插件在pathgeon管理之外。为此可以在安装时跳过 vimcdoc.vim 插件。 
可以使用 -I选项来安装：`./vimcdoc.sh -I`

4. 优先使用中文帮助
`set helplang=cn`

# 安装ctags cscope

```
    sudo apt-get install ctags
    sudo apt-get install cscope
```

# 常见问题

### no terminal library found

`sudo apt-get install libncurses5-dev`

### configure: error: no acceptable C compiler found in $PATH

`sudo apt-get install gcc`

