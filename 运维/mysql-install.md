
ubuntu 14.04 安装mysql 5.7

1. https://dev.mysql.com/downloads/mysql/
2.
下载：mysql-server_5.7.26-1ubuntu14.04_amd64.deb-bundle.tar
wget https://cdn.mysql.com//Downloads/MySQL-5.7/mysql-server_5.7.26-1ubuntu14.04_amd64.deb-bundle.tar

3. 解压tar包，按顺序安装

mysql-common_xxx-1ubuntu14.04_amd64.deb
mysql-community-client_xxx-1ubuntu14.04_amd64.deb
mysql-client_xxx-1ubuntu14.04_amd64.deb
mysql-community-server_xxx-1ubuntu14.04_amd64.deb
mysql-server_xxx-1ubuntu14.04_amd64.deb


# 依赖问题

1. Package libmecab2 is not installed.

sudo apt -get install libmecab2
