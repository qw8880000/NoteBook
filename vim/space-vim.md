
# windows 环境

* 安装phthon3后，加入环境变量
* 安装 LUA

* 安装gvim后，加入环境变量
* 安装git后，加入环境变量

* 安装字体[ DejaVu Sans Mono for Powerline ](https://github.com/powerline/fonts/tree/master/DejaVuSansMono)

## vimproc

vimproc这个vim插件需要使用gcc编译器进行编译，windows下可以使用MinGW作 为编译环境,这里使用[MinGW-W64 GCC-7.3.0](https://link.jianshu.com/?t=https%3A%2F%2Fsourceforge.net%2Fprojects%2Fmingw-w64%2Ffiles%2FToolchains%2520targetting%2520Win64%2FPersonal%2520Builds%2Fmingw-builds%2F7.3.0%2Fthreads-posix%2Fseh%2Fx86_64-7.3.0-release-posix-seh-rt_v5-rev0.7z)。

下载后解压，并将bin目录加入环境变量；MinGW提供的是`mingw32-make`，复制一份并重命名为`make`以便vimproc调用。

## 参考文章

[ Spacevim - windows ](https://www.jianshu.com/p/b817e5330cbe)

# tips

`:SPDebugInfo` 查看spacevim的调试信息。

`vim -V20logfile text.txt` 查看vim 启动信息。
