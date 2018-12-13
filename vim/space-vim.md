# Spacevim

github 地址：[SpaceVim/SpaceVim - github](https://github.com/SpaceVim/SpaceVim)

# windows 环境
  - 安装 python3，加入环境变量
  - 安装 python2，加入环境变量（可选，我没装，会报checking +python fail）
  - 安装 lua，加入环境变量
  - 安装 [gvim](https://github.com/vim/vim-win32-installer/releases)，加入环境变量
  - 安装 git，加入环境变量
  - 安装字体[ DejaVu Sans Mono for Powerline ](https://github.com/powerline/fonts/tree/master/DejaVuSansMono)

## vimproc

vimproc这个vim插件需要使用gcc编译器进行编译，windows下可以使用MinGW作 为编译环境,这里使用[MinGW-W64 GCC-7.3.0](https://link.jianshu.com/?t=https%3A%2F%2Fsourceforge.net%2Fprojects%2Fmingw-w64%2Ffiles%2FToolchains%2520targetting%2520Win64%2FPersonal%2520Builds%2Fmingw-builds%2F7.3.0%2Fthreads-posix%2Fseh%2Fx86_64-7.3.0-release-posix-seh-rt_v5-rev0.7z)。

下载后解压，并将bin目录加入环境变量；MinGW提供的是`mingw32-make`，复制一份并重命名为`make`以便vimproc调用。

## 参考文章
  - [ Spacevim - windows ](https://www.jianshu.com/p/b817e5330cbe)

# tips
  - `:SPDebugInfo` 查看spacevim的调试信息。
  - `vim -V20logfile text.txt` 查看vim 启动信息。
  - `vim --version` 或者在vim中使用`:version` 查看vim的编译选项，比如查看是否支持python
  - `:echo has('python')` 查看是否支持python
