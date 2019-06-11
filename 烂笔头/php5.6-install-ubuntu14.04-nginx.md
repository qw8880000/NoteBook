安装环境：
* ubuntu 14.04
* php5.6
* nginx 1.4.x

nginx不能处理php，而是转给php-fpm去处理。以下介绍php的安装与配置。

# 步骤

* 首先添加php官方源
```
sudo add-apt-repository ppa:ondrej/php
```

* 更新apt并安装php与php扩展
```
sudo apt-get update
sudo apt-get install php5 php5-mysql php5-curl php5-gd php5-intl php-pear php5-imagick php5-imap php5-mcrypt php5-memcache
sudo apt-get install php5-fpm
```

* 修改/etc/php5/fpm/php.ini文件
```
cgi.fix_pathinfo = 0;
```

* 修改 php-fpm.conf 配置文件，确保 php-fpm 模块使用 www-data 用户和 www-data 用户组的身份运行。
打开配置文件`/etc/php5/fpm/pool.d/www.conf`，修改：
```
; Unix user/group of processes
; Note: The user is mandatory. If the group is not set, the default user's group
;       will be used.
user = www-data
group = www-data
```

* 启动php-fpm
```
service php5-fpm start
```

* 修改nginx配置
打开`/etc/nginx/conf.d/`对应的你的web的配置文件，使其支持PHP请求被传送到后端的 PHP-FPM 模块：
```
location ~ \.php$ {
                fastcgi_split_path_info ^(.+\.php)(/.+)$;
        #       # NOTE: You should have "cgi.fix_pathinfo = 0;" in php.ini
        #       # With php5-fpm:
                fastcgi_pass unix:/run/php5-fpm.sock;
                fastcgi_index index.php;
                include fastcgi_params;
        }
```

* 重启nginx
```
nginx -s reload
```
