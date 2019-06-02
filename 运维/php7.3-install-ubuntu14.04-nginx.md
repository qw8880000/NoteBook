
安装环境：
* ubuntu 14.04
* php 7.3
* nginx 1.4.x

nginx不能处理php，而是转给php-fpm去处理。以下介绍php的安装与配置。

# 步骤

* 下载 [php-7.3.5](https://www.php.net/distributions/php-7.3.5.tar.gz)
* `tar -xzvf php-7.3.5.tar.gz`
* `cd php-7.3.5`
* 编译前配置
```
./configure --enable-fpm \
--enable-mysqlnd --with-pdo-mysql=mysqlnd --with-mysqli \
--with-zlib \
--with-curl \
--enable-mbstring \
--enable-xml \
--prefix=/usr/local/php7.3.5 --with-config-file-path=/usr/local/php7.3.5/ \
--disable-fileinfo
```
* 编译并安装
```
make
sudo make install
```

* 进行以下配置
```
cp php.ini-development /usr/local/php7.3.5/php.ini
cp /usr/local/php7.3.5/etc/php-fpm.d/www.conf.default /usr/local/php7.3.5/etc/php-fpm.d/www.conf
cp /usr/local/php7.3.5/sbin/php-fpm /usr/local/bin
```

* 修改 php-fpm.d/www.conf 配置文件，确保 php-fpm 模块使用 www-data 用户和 www-data 用户组的身份运行。
```
; Unix user/group of processes
; Note: The user is mandatory. If the group is not set, the default user's group
;       will be used.
user = www-data
group = www-data
```

* 修改php.ini文件
```
vim /usr/local/php7.3.5/php.ini
cgi.fix_pathinfo=0
```

* 启动php-fpm
```
sudo php-fpm -y /usr/local/php7.3.5/etc/php-fpm.conf -p /usr/local/php7.3.5
```

# 遇到的问题

* 问题：configure: error: libxml2 not found. Please check your libxml2 installation.
解决：sudo apt-get install libxml2-dev

* make: *** [ext/fileinfo/libmagic/apprentice.lo] Error 1
解决：内存不足，./configure 增加--disable-fileinfo参数

* ERROR: failed to open error_log (/usr/local/php7.3.5/log/php-fpm.log): No such file or directory (2)
解决：mkdir /usr/local/php7.3.5/log

* configure: error: Please reinstall the libcurl distribution - easy.h should be in <curl-dir>/include/curl/
解决：安装curl
```
下载[curl](https://curl.haxx.se/download/curl-7.64.1.tar.gz)
./configure。
make
make install
```

* 找不到zlib
```
下载[zlib](http://www.zlib.net/zlib-1.2.11.tar.gz)
./configure
make
sudo make install
```

# 参考

参考：https://www.php.net/manual/zh/install.unix.nginx.php
