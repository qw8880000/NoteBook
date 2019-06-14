
ftk核心源码在src目录下：
```
src/*.c
src/backend/native/*.c
src/os/linux/*.c
```
编写Makefile，编译src下的所有C文件，其他的都是非必须的，可以先去掉，减少编译复杂度。

# 常见问题   

* 函数或变量重定义
例如:ftk_font_freetype.c 与 ftk_font_default.c 里面提供的函数接口都一样，但是具体实现不一样，我们可以选一种自己需要的实现；如果我们需要的是ftk_font_default.c那就把ftk_font_freetype.c删除掉  
