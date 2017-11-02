---
title: vim第一个要安装的插件 - vundle
date: 2017-11-01 17:20:57
categories:
    - vim
tags:
    - vim
abbrlink: 5faad70a8691ab64
---

[vundle](https://github.com/VundleVim/Vundle.vim), 我写这篇文章的时候，这个插件在github上有16103个星星，不明觉历。

vundle简单来说就是vim的插件管理器，帮你管理插件的安装，删除，更新。你只需要在配置中填入你要安装的插件名称，再执行安装命令就能帮你安装所有插件。

# 安装

```sh
    mkdir ~/.vim
    git clone https://github.com/gmarik/vundle.git ~/.vim/bundle/vundle
```

安装完vundle插件后，就可以用来管理其他插件了

# 配置插件

把你需要安装的插件放在`.vimrc`的开头部分，以下是例子：

```vim
set nocompatible              " be iMproved, required
filetype off                  " required

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'

" The following are examples of different formats supported.
" Keep Plugin commands between vundle#begin/end.
" plugin on GitHub repo
Plugin 'tpope/vim-fugitive'
" plugin from http://vim-scripts.org/vim/scripts.html
" Plugin 'L9'
" Git plugin not hosted on GitHub
Plugin 'git://git.wincent.com/command-t.git'
" git repos on your local machine (i.e. when working on your own plugin)
Plugin 'file:///home/gmarik/path/to/plugin'
" The sparkup vim script is in a subdirectory of this repo called vim.
" Pass the path to set the runtimepath properly.
Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
" Install L9 and avoid a Naming conflict if you've already installed a
" different version somewhere else.
" Plugin 'ascenator/L9', {'name': 'newL9'}

" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required
" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
"
" see :h vundle for more details or wiki for FAQ
" Put your non-Plugin stuff after this line
```

# 安装其他插件 

打开vim并运行`:PluginInstall`

