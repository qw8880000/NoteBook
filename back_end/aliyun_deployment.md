
# 常用应用部署

## 安装Git

`sudo apt-get install git`

## 安装nginx

https://www.nginx.com/resources/wiki/start/topics/tutorials/install/

安装nginx: `sudo apt-get install nginx`

升级nginx:
1. 查看原nginx参数: `nginx -V`，我的参数是：
`configure arguments: --with-cc-opt='-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security -D_FORTIFY_SOURCE=2' --with-ld-opt='-Wl,-Bsymbolic-functions -Wl,-z,relro' --prefix=/usr/share/nginx --conf-path=/etc/nginx/nginx.conf --http-log-path=/var/log/nginx/access.log --error-log-path=/var/log/nginx/error.log --lock-path=/var/lock/nginx.lock --pid-path=/run/nginx.pid --http-client-body-temp-path=/var/lib/nginx/body --http-fastcgi-temp-path=/var/lib/nginx/fastcgi --http-proxy-temp-path=/var/lib/nginx/proxy --http-scgi-temp-path=/var/lib/nginx/scgi --http-uwsgi-temp-path=/var/lib/nginx/uwsgi --with-debug --with-pcre-jit --with-ipv6 --with-http_ssl_module --with-http_stub_status_module --with-http_realip_module --with-http_addition_module --with-http_dav_module --with-http_geoip_module --with-http_gzip_static_module --with-http_image_filter_module --with-http_sub_module --with-http_xslt_module --with-mail --with-mail_ssl_module --with-file-aio --with-http_v2_module`
1. 下载nginx:`wget http://nginx.org/download/nginx-1.9.12.tar.gz`
1. 解压：`tar -zxvf nginx-1.9.12.tar.gz`
1. `cd nginx-1.9.12`
1. `./configure --with-cc-opt='-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security -D_FORTIFY_SOURCE=2' --with-ld-opt='-Wl,-Bsymbolic-functions -Wl,-z,relro' --prefix=/usr/share/nginx --conf-path=/etc/nginx/nginx.conf --http-log-path=/var/log/nginx/access.log --error-log-path=/var/log/nginx/error.log --lock-path=/var/lock/nginx.lock --pid-path=/run/nginx.pid --http-client-body-temp-path=/var/lib/nginx/body --http-fastcgi-temp-path=/var/lib/nginx/fastcgi --http-proxy-temp-path=/var/lib/nginx/proxy --http-scgi-temp-path=/var/lib/nginx/scgi --http-uwsgi-temp-path=/var/lib/nginx/uwsgi --with-debug --with-pcre-jit --with-ipv6 --with-http_ssl_module --with-http_stub_status_module --with-http_realip_module --with-http_addition_module --with-http_dav_module --with-http_geoip_module --with-http_gzip_static_module --with-http_image_filter_module --with-http_sub_module --with-http_xslt_module --with-mail --with-mail_ssl_module --with-file-aio --with-http_v2_module`

问题：
`./configure: error: invalid option "--with-http_spdy_module"` 解决：`--with-http_spdy_module`换成`--with-file-aio --with-http_v2_module`

`./configure: error: the HTTP rewrite module requires the PCRE library.` 解决：`sudo apt-get install libpcre3 libpcre3-dev`

`./configure: error: the HTTP XSLT module requires the libxml2/libxslt` 解决：`sudo apt-get install libxml2 libxml2-dev libxslt-dev`

`./configure: error: the HTTP image filter module requires the GD library.` 解决：

设置nginx开机启动(有可能不需要设置)：
1. `/etc/init.d/` 新建一个文件，叫做`myscript`
1. `myscript`中写入启动nginx的命令
1. `chmod ugo+x /etc/init.d/myscript`
1. `update-rc.d myscript defaults`

nginx反向代理设置:
1. 

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

