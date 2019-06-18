
# CMake 简介

CMake 是一个跨平台的自动化建构系统，它使用一个名为 CMakeLists.txt 的文件来描述构建过程，可以产生标准的构建文件，如 Unix 的 Makefile 或Windows Visual C++ 的 projects/workspaces 。

文件 CMakeLists.txt 需要手工编写,也可以通过编写脚本进行半自动的生成。

CMake 是一个比 automake 更加容易使用的工具，提供了比 autoconf 更简洁的语法。

# CMake 用法

* 编写 CmakeLists.txt。
* 执行命令“cmake PATH”或者“ccmake PATH”生成 Makefile ( PATH 是 CMakeLists.txt 所在的目录 )。
* 使用 make 命令进行编译。

# 参考

* [cmake 主页](https://cmake.org/)
* [cmake - wikipedia](https://zh.wikipedia.org/zh-cn/CMake)
* [在 linux 下使用 CMake 构建应用程序](https://www.ibm.com/developerworks/cn/linux/l-cn-cmake/)
* [cmake实践.pdf](http://sewm.pku.edu.cn/src/paradise/reference/CMake%20Practice.pdf)
