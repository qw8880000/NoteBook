
```
@author: wangjl
@date: 2017-06-20
```

# libdvp

libdvp 公共代码库:
`git@192.168.61.223:dvp-common/libdvp.git`

# git 在公共代码库上的使用

我们把ds2000/ds2600/ds3000上关于dvp的代码抽出来，合并成一个公共的代码库`libdvp`。

也就是服务器上将存在以下4个相互独立的代码仓库：

```
服务器
    |-- ds2000.git              // ds2000 的 SDK
    |-- ds2600.git              // ds2600 的 SDK
    |-- ds3000.git              // ds3000 的 SDK
    \-- libdvp.git              // dvp 库
```

这里，我们把`libdvp.git` 作为 `ds2000.git/ds2600.git/ds3000.git` 的子项目，需要用到工具`git subtree`。

### git subtree 的使用

这里以ds2600为例子。

1. 添加远程仓库到`ds2600.git`

语法：`git remote add -f <子仓库名> <子仓库地址>`

实例：`git remote add -f libdvp git@192.168.61.223:dvp-common/libdvp.git`

验证：`git remote -v` 可以看到已经你添加成功了一个新的远程仓库叫 `libdvp`

1. `libdvp.git` 引入作为`ds2600.git` 的子项目。

语法：`git subtree add --prefix=<子目录名> <子仓库名> <分支> --squash`

实例：`git subtree add --prefix=camdroid/device/softwinner/tiger-app/dvp_lib/libdvp libdvp master --squash`

注意：执行`git subtree`需要在`ds2600.git` 的根路径上；`--prefix`参数用来指明libdvp的存放位置；`--squash`用于
把libdvp的提交记录合并成一个，可不加。

1. 拉取更新(`git subtree pull`)

语法：`git subtree pull --prefix=<子目录名> <子仓库名> <分支> --squash`

实例：`git subtree pull --prefix=camdroid/device/softwinner/tiger-app/dvp_lib/libdvp libdvp develop`

上述命令将会从`libdvp.git`的`develop`分支拉取更新到`ds2600.git` 的libdvp子项目。

1. 推送更新(`git subtree push`)

语法：`git subtree push --prefix=<子目录名> <子仓库名> <分支> --squash`

实例：`git subtree push --prefix=camdroid/device/softwinner/tiger-app/dvp_lib/libdvp libdvp develop`

上述命令将会把`ds2600.git`中关于libdvp子项目的修改推送到`libdvp.git`仓库。

参考：
* [Git Subtree的使用](http://www.jianshu.com/p/84e34ac318e4)

### (git pull & push) 与 (git subtree pull & push) 的区别

这里以ds2600为例子。

对于libdvp中的修改，(git pull & push) 与 (git subtree pull & push) 是有区别的

git pull & push
```
本地ds2600.git              服务器ds2600.git
    |                           |
  libdvp      ---git push-->  libdvp
              <---git pull--  
```

git subtree pull & push
```
本地ds2600.git                          服务器libdvp.git
    |                                       |
  libdvp      ---git subtree push-->       libdvp
              <---git subtree pull--  
```

# libdvp的目录结构

libdvp的目录结构沿续之前的结构，

```
dvp_lib
    |-- config
    |-- platform
    |-- framework
    |-- task
    |-- ...
    |-- utils
    \-- libdvp
            |-- config
            |-- platform
            |-- framework
            |-- task
            |-- ...
            \-- utils
```

把原dvp_lib的代码慢慢统一，移向libdvp，最终变成：

```
dvp_lib
    |
    \-- libdvp
            |-- config
            |-- platform
            |-- framework
            |-- task
            |-- ...
            \-- utils
```

这个过程中，dvp_lib从外部看上去是没有变化的。

# 依赖于具体平台的代码怎么统一

依赖于具体平台的代码无法统一，需要借助编译宏来隔离。

* ds2000 的编译宏是 `SDK_VERSION_2000`
* ds2600 的编译宏是 `SDK_VERSION_2600`
* ds3000 的编译宏是 `SDK_VERSION_3000`

如，文件的存放路径在各平台中有差异，利用编译宏来区分(见`file_path.h`)：
```
#if defined SDK_VERSION_3000

#include "dvp_file_path/dvp_file_path.h"

#define FILE_ELE_MAP_CONFIG     DVP_E_SW_CFG_ELE_MAP_FILE
#define FILE_ELE_CONFIG_XML     DVP_SW_CFG_DIR"etc/elevator/ele_config.xml"

#elif defined SDK_VERSION_2600

#include "dvp_file_path/dvp_file_path.h"

#define FILE_ELE_MAP_CONFIG     SW_CFG_ETC_ELE_MAP_CONF
#define FILE_ELE_CONFIG_XML     SW_CFG_ETC_ELE_DIR"ele_config.xml"

#elif defined SDK_VERSION_2000

#define FILE_ELE_MAP_CONFIG     DVP_E_SW_CFG_ELE_MAP_FILE
#define FILE_ELE_CONFIG_XML     DVP_E_SW_CFG_ELE_CONFIG

#endif

```


