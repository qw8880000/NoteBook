
# 如何安装不同版本的node.js

需要第三方软件的支持：
- windows下node.js的版本管理：[coreybutler/nvm-windows - Github](https://github.com/coreybutler/nvm-windows)
- linux下node.js的版本管理：[creationix/nvm - Github](https://github.com/creationix/nvm)

关于windows版本的nvm，在下载node.js的时候经常会因为网络问题很慢，通常的做法就是下载node.js的二进制包，然后放在对应的目录下面去。例如：
1. 下面node.js二进制软件包 `node-v10.15.0-win-x64.zip`
1. 解压上述压缩包，重命名为`v10.15.0`
1. 通过`nvm root`命令找到当前保存node.js软件包的路径，并将`v10.15.0`放在里面
