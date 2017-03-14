@Filename:       automake.md  
@Author:         wangjl  
@Date:           2016-10-12 11:29  
@Description:    

# automake 简介

autoconf/automake主要用于创建Makefile.

automake 相关工具：

-   aclocal     :根据configure.ac生成aclocal.m4文件
-   autoscan    :以生成一个configure.in的样板文件
-   autoconf    :根据configure.in(configure.ac)生成configure
-   autoheader  :
-   automake    :根据 Makefile.am 生成Makefile.in

# 安装automake

`sudo apt-get install automake`

# 能力进阶

### autoconf手册

-   [autoconf 英文手册](https://www.gnu.org/software/autoconf/manual/autoconf.html)

### automake手册

-   [automake 英文手册](https://www.gnu.org/software/automake/manual/automake.html)

### Makefile.am 语法 

-   [Makefile.am 规则和实例详解](http://www.ivpeng.com/pblog/makefile-am.html)

# 参考

-   [linux 下 automake 使用教程](https://loftor.com/archives/automake.html)
-   [例解 autoconf 和 automake 生成 Makefile 文件](https://www.ibm.com/developerworks/cn/linux/l-makefile/)
-   [ automake,autoconf使用详解](http://www.laruence.com/2009/11/18/1154.html)
-   [运用Autoconf和Automake生成Makefile的学习之路](http://www.cnblogs.com/ericdream/archive/2011/12/09/2282359.html)
-   [autotools 入门](http://leolovenet.com/downloads/files/autotools.pdf)
-   [automake 和 autoconf 使用简明教程](http://thebigdoc.readthedocs.io/en/latest/auto-make-conf.html)

# automake 学习

-   aclocal     :根据configure.ac生成aclocal.m4文件
-   autoscan    :以生成一个configure.in的样板文件
-   autoconf    :根据configure.in(configure.ac)生成configure
-   autoheader  :
-   automake    :根据 Makefile.am 生成Makefile.in
-   Makefile.am :Makefile.am是用来生成Makefile.in的 ,需要你手工书写.Makefile.am

### configure.ac 示例

    # Process this file with Autoconf to produce a configure script.   
    AC_INIT(Main.cpp)       #指定main函数所在的文件  
    AM_INIT_AUTOMAKE(hello, 1.0)    #指定程序名称和版本  
    # Checks for programs.  
    #检查可用的编译器  
    AC_PROG_CC          #C语言编译器  
    AC_PROG_CPP         #C++编译器  
    AC_PROG_CXX  
    # Checks for libraries.   
    # Checks for header files.   
    # Checks for typedefs, structures, and compiler characteristics.   
    # Checks for library functions.   
    AC_OUTPUT(Makefile)

### Makefile.am 示例

    AUTOMAKE_OPTIONS=foreign
    bin_PROGRAMS=hello
    hello_SOURCES=hello_world.c

## 步骤

参考：[Configure，Makefile.am, Makefile.in, Makefile文件之](https://my.oschina.net/qihh/blog/66113)

1. autoscan 

    autoscan 后， 生成configure.scan; 
    修改configure.scan 生成configure.ac

1. aclocal

    根据configure.ac 生成aclocal.m4

1. autoheader

    根据 configure.ac 与 aclocal.m4 生成config.h.in

1. autoconf

    根据 configure.ac 与 aclocal.m4 生成configure

1. 编写Makefile.am

1. automake --add-missing

    根据Makefile.am 与 configure.ac 生成 Makefile.in

1. ./configure

    根据Makefile.in 与 config.h.in 生成 config.h 与 Makefile

1. make 
1. make install


