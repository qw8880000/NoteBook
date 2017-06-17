

## google test

Google Test, Google's C++ test framework!

源码：
* [ google test ](https://github.com/google/googletest)

## google test 目录结构

```
googlemock
googletest
    |-- src/                // Google test Framework 源码
    |-- include/            // Google test Framework 源码的头文件 
    |
    |-- docs/               // documentations for Google Test
    |-- scripts/            // 一些脚本用于产生测试用例的
    |-- samples/            // 示例程序，展示如何使用Google test 的特性
    |-- test/               // 用来测试google test 源码的代码
    |
    |-- build-aux/
    |-- cmake/              // CMake 相关
    |-- CMakeLists.txt      // CMake 相关
    |-- m4/                 // automake 自动生成目录
    |
    |-- msvc/               // 针对Microsoft Visual C++ 的 gtest的工程文件 
    |-- codegear/           // 针对codegear 的gtest 工程文件 
    |-- make/               // 针对linux的Makefile
    \-- xcode/              // 针对Xcode projects on Mac OS X 的 gtest 工程文件
```


## googlemock 在 C 上的使用

* [Using GoogleTest and GoogleMock frameworks for embedded C](https://www.codeproject.com/articles/1040972/using-googletest-and-googlemock-frameworks-for-emb)

## 参考

* [Linux下Google Test （GTest）测试环境搭建步骤](http://www.linuxidc.com/Linux/2015-05/116894.htm)
* [玩转Google开源C++单元测试框架Google Test系列(gtest)(总)](http://www.cnblogs.com/coderzh/archive/2009/04/06/1426755.html)

