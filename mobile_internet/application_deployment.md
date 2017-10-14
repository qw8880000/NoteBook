
```

应用部署
    |
    |-- nginx
    |   |
    |   |-- [Nginx中文文档](http://www.nginx.cn/doc/)
    |   \-- nginx 反向代理
    |
    \-- 虚拟主机
        | 
        |-- 虚拟主机，就是让多个网站共享使用同一服务器同一IP地址，通过域名的不同来划分请求。主流的HTTP服务器都提供了虚拟主机支持，如Nginx、Apache、IIS等
        \-- 为了共享80端口

```


# 应用部署

### 安装Git

### 安装VIM

### nginx 安装

### 设置nginx开机启动

方法一：
把启动脚本放入 `/etc/rc.local`

方法二： 
1. `vi /etc/init.d/myscript`
1. `chmod ugo+x /etc/init.d/myscript`
1. `update-rc.d myscript defaults`

### 安装node.js

### node.js 版本升级

1. `npm install -g n`
1. `n latest`

### npm 相关

指定npm安装源
`npm install -g --registry=https://registry.npm.taobao.org`

使用`nrm` 切换npm 默认源：
1. `npm install -g nrm`
1. `nrm use taobao`

### 安装PM2

`$ npm install pm2 -g`

### ftp

http://www.cnblogs.com/angus1121/p/5056398.html
https://help.aliyun.com/document_detail/51998.html?spm=5176.doc58746.2.10.pltfPp
