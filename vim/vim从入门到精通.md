@Filename:       vim从入门到精通.md  
@Author:         wangjl  
@Date:           2016-09-22 22:31  
@Description:    

# 新建.vimrc

    touch ~/.vimrc

[vim 配置 example](https://github.com/VundleVim/Vundle.vim/wiki/Examples)

# 查看vim帮助

输入：

    :help

看到关键字，使用以下快捷键可以跳转到对应章节：

    ctrl + ]

# 分割窗口

水平分割：

    :vsplit

垂直分割：

    :vertical

# 切换窗口

原快捷键：

    

# 更换配色方案

方法：

    1. mkdir ~/.vim/colors
    1. 把配色方案放到这下面
    1. .vimrc中加入 colorscheme  方案名

        syntax on
        syntax enable
        set t_Co=256
        colorscheme molokai

我喜欢的配色方案：

    molokai.vim
    jellybeans.vim
    Tomorrow-Night-Eighties.vim
    
# 安装vundle插件

    mkdir ~/.vim
    git clone https://github.com/gmarik/vundle.git ~/.vim/bundle/vundle

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
可是使用 -I选项来安装：

    `./vimcdoc.sh -I`

4. 优先使用中文帮助

    `set helplang=cn`

# 安装ctags cscope

...



# 参考 
* [ 到底 VIM 能配置到多强大的程度？ ](https://www.zhihu.com/question/20151659)
