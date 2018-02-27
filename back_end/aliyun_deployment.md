
# 常用应用部署

## 安装Git

`sudo apt-get install git`

## 安装nginx

参考安装方式：[nginx install - nginx wiki](https://www.nginx.com/resources/wiki/start/topics/tutorials/install/).

1. 把nginx源加入到安装源里`/etc/apt/sources.list`，如果不想修改上述源，可以在`/etc/apt/sources.list.d/`下面新增文件，如`/etc/apt/sources.list.d/nginx.list`。
```
## Replace $release with your corresponding Ubuntu release.
deb http://nginx.org/packages/ubuntu/ $release nginx
deb-src http://nginx.org/packages/ubuntu/ $release nginx
```
例如ubuntu 14.04(Trusty):
```
deb http://nginx.org/packages/ubuntu/ trusty nginx
deb-src http://nginx.org/packages/ubuntu/ trusty nginx
```

2. 执行以下命令：
```
sudo apt-get update
sudo apt-get install nginx
```

如果出现 `W: GPG error: http://nginx.org trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY $key`，执行以下操作：
```
## Replace $key with the corresponding $key from your GPG error.
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys $key
sudo apt-get update
sudo apt-get install nginx
```

3. 执行`nginx -v` 查看是否安装成功

## 安装node.js

## node.js 版本升级

1. `npm install -g n`
1. `n latest`

## npm 相关

指定npm安装源
`npm install -g --registry=https://registry.npm.taobao.org`

使用`nrm` 切换npm 默认源：
1. `npm install -g nrm`
1. `nrm use taobao`

## ftp

[云服务器 ECS 配置：云服务器ECS下的FTP服务的安装配置与使用](https://yq.aliyun.com/articles/170003)

1. ecs主机开启安全组 `20/21` 入方向端口
1. ecs主机开启安全组 `1024-65535` 入方向端口(由于ftp在服务器中只能使用主动模式，所以外往连接时使用的随机端口进行连接)
1. `apt-get install vsftpd` 安装vsftpd


1. `ufw disable` 确保防火墙关闭
1. `/etc/ftpusers` 表示不能使用ftp的帐户
1. `ftp localhost` 本地测试ftp服务是否正常
1. `telnet [ip] [port]` 远程测试主机的端口是否打开
1. `netstat -tnlp` 查看vsftpd 是否监听的是 `0.0.0.0` 的 `21` 端口

相关文件：
1. `/etc/vsftpd.conf`
1. `/etc/ftpusers`
1. `/etc/shells`

vsftpd命令：
1. `service vsftpd restart`

# 其他

## 安装Ruby

Ruby is best installed either via [RVM](https://rvm.io/).

* install RVM:
    * `gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB`
    * `\curl -sSL https://get.rvm.io | bash -s stable`
    * logout and then login again

* 安装 ruby:`rvm install 2.2.0`
* 切换 ruby版本:`rvm use 2.2.0`

## 安装gollum

markdown wiki [gollum](https://github.com/gollum/gollum).

安装 gollum:
* 安装ruby 
* `gem install gollum`
* 安装git

常见问题:
执行`gem install gollum`后提示：`ERROR: Failed to build gem native extension`.  
解决：`sudo apt-get install libicu-dev`.

## 安装PM2

`$ npm install pm2 -g`

