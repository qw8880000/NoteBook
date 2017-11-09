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
```sh
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
```sh
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

```sh
make 
sudo make install
```

# 确认是否安装成功

终端下输入 vim ，如果无错误信息即可

# 把vim作为默认编辑器

```sh
sudo update-alternatives --install /usr/bin/editor editor /usr/bin/vim 1 
sudo update-alternatives --set editor /usr/bin/vim
sudo update-alternatives --install /usr/bin/vi vi /usr/bin/vim 1 
sudo update-alternatives --set vi /usr/bin/vim
```

# 更换配色方案

参考: [vim设置配色主题](http://www.wangjinle.com/posts/207a3e1fac90dec3.html)

# 安装vundle插件

参考: [vim第一个要安装的插件 - vundle](http://www.wangjinle.com/posts/5faad70a8691ab64.html)

# 安装中文帮助

参考: [vim安装中文帮助](http://www.wangjinle.com/posts/0d1f184e23815ff1.html)

# 安装ctags cscope

```sh
sudo apt-get install ctags
sudo apt-get install cscope
```

# 常见问题

### no terminal library found

`sudo apt-get install libncurses5-dev`

### configure: error: no acceptable C compiler found in $PATH

`sudo apt-get install gcc`

# 更多

更多内容参考：[vim学习汇总](http://www.wangjinle.com/posts/9a88772f17a949d5.html)
