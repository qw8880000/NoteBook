

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

1. 访问wordpress安装页面：http://example.com/wp-admin/install.php


您的PHP似乎没有安装运行WordPress所必需的MySQL扩展。
https://my.oschina.net/u/1266171/blog/778939
