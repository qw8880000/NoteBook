@Filename:       ftk_to_Ubuntu_移植.md    
@Author:         wangjl    
@Date:           2015-11-25 20:34    
@Last modified:  2015-11-25 20:34    
@Description:     
  
  
# ftk移植
  
这里以移植到Ubuntu为例子。
  
#### 1.编译ftk库：  
  
ftk核心源码：src目录  
  
编写Makefile，编译src下的所有C文件  
  
其中ftk/src下主要的源文件：  
```  
src/*.c  
src/backend/native/*.c  
src/os/linux/*.c  
```  
其他的都是非必须的，可以先去掉，减少编译复杂度。  
  
#### 2.解决编译常见问题   
  
* error: jpeglib.h: No such file or directory  
    apt-get install libjpeg62-dev  
* error: png.h: No such file or directory  
    apt-get install libpng-dev  
* 函数或变量重定义  
    例如:ftk_font_freetype.c 与 ftk_font_default.c 里面提供的函数接口都一样，但是具体实现不一样，我们可以选一种自己需要的实现；  
    如果我们需要的是ftk_font_default.c那就把ftk_font_freetype.c删除掉  
  
### 使用ftk的demo  

从ftk源码里的demo中选一个编译后，运行。  
如何使用ubuntu的framebuffer运行ftk_demo > 见底下附1  

# 附1  
  
```  
直接在Ubuntu上运行Framebuffer  
  
默认Ubuntu是直接进入X视窗，如果要使用Framebuffer，  
  
需要修改内核引导参数：  
  
$ sudo gedit /etc/default/grub  
  
查找  
  
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"  
  
把它改为  
  
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text vga=0x311"   
  
这里text表示进入文本模式，vga=0x311表示使用Framebuffer显示驱动，  
  
0x311是指示色深和分辨率的参数  
  
  |640x480 800x600 1024x768 1280x1024  
  
----+-------------------------------------  
  
256 | 0x301   0x303 0x305 0x307  
  
32k | 0x310   0x313 0x316 0x319  
  
64k | 0x311   0x314 0x317 0x31A  
  
16M | 0x312   0x315 0x318 0x31B  
  
如果使用vga=0x311参数，必须使用后面提到的vesafb模块，并且取消黑名单，  
  
否则无法进入系统，需要光盘启动删除vga参数以还原  
  
$ sudo update-grub  
  
写入到/boot/grub/grub.cfg  
  
$ sudo gedit /etc/initramfs-tools/modules  
  
在其中加入：vesafb  
  
$ sudo gedit /etc/modprobe.d/blacklist-framebuffer.conf  
  
用#注释以下行  
  
# blacklist vesafb  
  
$ sudo update-initramfs -u  
  
（生成新的initrd）  
  
然后重启机器，即可进入Framebuffer  
  
如果要切换回X11，可以输入：  
  
$ startx  
  
有时候/boot/grub/grub.cfg的引导参数不正确导致系统无法引导，  
  
可以用光盘引导系统，挂载硬盘后直接修改/boot/grub/grub.cfg文件  
  
这样就可以跳过update-grub这一步。然后还原原有的引导参数进入X Window  
```  
