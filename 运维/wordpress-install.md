
# wordpress安装

1. 下载并解压缩WordPress程序安装包
1. 安装mysql 5.7，并创建数据库与账户
```
CREATE DATABASE wordpress;
GRANT ALL PRIVILEGES ON wordpress.* TO 'username'@'host' IDENTIFIED BY 'password';
FLUSH PRIVILEGES;
```
1. 重命名 wp-config-sample.php 文件为 wp-config.php
1. 设置wp-config.php文件，输入数据库信息
```
DB_NAME=wordpress
DB_USER=username
DB_PASSWORD=password
DB_HOST=localhost
```

1. nginx 配置 修改 nginx 配置nginx/conf.d/wordpress.conf
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

1. 访问wordpress安装页面：http://example.com/wp-admin/install.php


您的PHP似乎没有安装运行WordPress所必需的MySQL扩展。
https://my.oschina.net/u/1266171/blog/778939

# 插件

* WP Editor.md：WP Editor.MD is a beautiful and practical Markdown document editor.
* Markdown Github：A plugin to inject markdown files directly into a post from Github.
* WP Githuber MD:WordPress Markdown Editor
* Mytory Markdown: The plugin get markdown file URL like github raw content url. It convert markdown file to html, and put it to post content.


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
