在ubuntu 14.04上安装mysql 5.7.26，以下是安装步骤。

# 安装

* 访问[mysql - download](https://dev.mysql.com/downloads/mysql/)，找到mysql的安装包地址

* 下载`mysql-server_5.7.26-1ubuntu14.04_amd64.deb-bundle.tar`
```
wget https://cdn.mysql.com//Downloads/MySQL-5.7/mysql-server_5.7.26-1ubuntu14.04_amd64.deb-bundle.tar
```

* 解压tar包
```
tar -xzvf mysql-server_5.7.26-1ubuntu14.04_amd64.deb-bundle.tar
```

* 按顺序安装
```
dpkg -i mysql-common_xxx-1ubuntu14.04_amd64.deb
dpkg -i mysql-community-client_xxx-1ubuntu14.04_amd64.deb
dpkg -i mysql-client_xxx-1ubuntu14.04_amd64.deb
dpkg -i mysql-community-server_xxx-1ubuntu14.04_amd64.deb
dpkg -i mysql-server_xxx-1ubuntu14.04_amd64.deb
```

* 启动mysql
```
service mysql start
```

# 问题

* Package libmecab2 is not installed.
解决：`sudo apt -get install libmecab2`
