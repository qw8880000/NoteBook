
安装环境：
* ubuntu 14.04
* php 5.6
* nginx 1.4.x
* wordpress 5.0

# 安装简介

安装wordpress可直接查看[wordpress安装指南-官方](https://codex.wordpress.org/zh-cn:%E5%AE%89%E8%A3%85_WordPress)，这里只是记录我在ubuntu 14.04上的安装过程，作为备忘。

# 安装

* 安装mysql 5.7，参考[mysql 5.7在ubuntu 14.04上的安装](http://blog.wangjinle.com/?p=1487&preview=true)

* 创建WordPress数据库和一个用户
```
CREATE DATABASE wordpress;
GRANT ALL PRIVILEGES ON wordpress.* TO 'username'@'host' IDENTIFIED BY 'password';
FLUSH PRIVILEGES;
```

* 安装php5.6，参考[ubuntu 14.04 nginx 1.4.x环境安装php5.6](http://blog.wangjinle.com/article/php5-6-install-ubuntu14-04-nginx.html)

* 下载并解压缩WordPress程序安装包
* 重命名 wp-config-sample.php 文件为 wp-config.php
* 设置wp-config.php文件，输入数据库信息
```
DB_NAME=wordpress
DB_USER=username
DB_PASSWORD=password
DB_HOST=localhost
```

* 安装nginx
* nginx 配置 修改 nginx 配置nginx/conf.d/wordpress.conf
```
location ~ \.php$ {
                fastcgi_split_path_info ^(.+\.php)(/.+)$;
        #       # NOTE: You should have "cgi.fix_pathinfo = 0;" in php.ini
        #
        #       # With php5-cgi alone:
        #       fastcgi_pass 127.0.0.1:9000;
        #       # With php5-fpm:
                fastcgi_pass unix:/run/php/php5.6-fpm.sock;
                fastcgi_index index.php;
                include fastcgi_params;

				# php 7.x
        #       fastcgi_index index.php;
        #       fastcgi_pass    127.0.0.1:9000;
        #       include fastcgi_params;
        #       fastcgi_param   SCRIPT_FILENAME    $document_root$fastcgi_script_name;
        #       fastcgi_param   SCRIPT_NAME        $fastcgi_script_name;
        }
```

* 访问wordpress安装页面：http://example.com/wp-admin/install.php

# 问题

* 无法建立目录wp-content/uploads/2019/05。有没有上级目录的写权限？
启动nginx的用户为www-data，我的wordpress目录权限为nicer:nicer。把wordpress目录权限改成www-data:www-data即可

* 访问文章链接，提示nginx 404
设置nginx伪静态规则：
```
location / {
	try_files $uri $uri/ /index.php?$args;
}
```
