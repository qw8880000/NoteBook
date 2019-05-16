# ubuntu 14.04安装php5.6

1. 首先添加php官方源
sudo add-apt-repository ppa:ondrej/php

1. sudo apt-get update

1. sudo apt-get install php5.6

# ubuntu 14.04安装php7.3

参考：https://www.php.net/manual/zh/install.unix.nginx.php

1. 下载https://www.php.net/distributions/php-7.3.5.tar.gz
1. tar -xzvf php-7.3.5.tar.gz
1. cd php-7.3.5
1. ./configure --enable-fpm --enable-mysqlnd --with-pdo-mysql=mysqlnd --with-mysqli --prefix=/usr/local/php7.3.5 --with-config-file-path=/usr/local/php7.3.5/ --disable-fileinfo


1. make
1. sudo make install

配置文件
1. cp php.ini-development /usr/local/php7.3.5/php.ini
1. cp /usr/local/php7.3.5/etc/php-fpm.d/www.conf.default /usr/local/php7.3.5/etc/php-fpm.d/www.conf
1. cp /usr/local/php7.3.5/sbin/php-fpm /usr/local/bin

修改 php-fpm.d/www.conf 配置文件，确保 php-fpm 模块使用 www-data 用户和 www-data 用户组的身份运行。
```
; Unix user/group of processes
; Note: The user is mandatory. If the group is not set, the default user's group
;       will be used.
user = www-data
group = www-data
```


vim /usr/local/php/php.ini
cgi.fix_pathinfo=0

启动php-fpm
sudo php-fpm -y /usr/local/php7.3.5/etc/php-fpm.conf -p /usr/local/php7.3.5



问题：configure: error: libxml2 not found. Please check your libxml2 installation.
解决：sudo apt-get install libxml2-dev

make: *** [ext/fileinfo/libmagic/apprentice.lo] Error 1
内存不足，./configure 增加--disable-fileinfo参数

ERROR: failed to open error_log (/usr/local/php7.3.5/log/php-fpm.log): No such file or directory (2)
解决：mkdir /usr/local/php7.3.5/log
