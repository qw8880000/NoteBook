# service

## 简介

service命令用于对系统服务进行管理，比如启动（start）、停止（stop）、重启（restart）、查看状态（status）等。相关的命令还包括chkconfig、ntsysv等，chkconfig用于查看、设置服务的运行级别，ntsysv用于直观方便的设置各个服务是否自动启动。service命令本身是一个shell脚本，它在/etc/init.d/目录查找指定的服务脚本，然后调用该服务脚本来完成任务。service脚本最少需要实现 start 与 stop 命令。

## 常用指令

* service <service>：查看指定服务的使用帮助
* service <service> <command>：以指定命令执行指定服务脚本
* service --status-all: 以status命令执行所有服务脚本

例子：
1. `service network` 查看network服务的使用帮助：`/etc/init.d/network {start|stop|restart|reload|status}`
2. ` service network status` 执行network服务中的status命令，查看网络状态
3. `service network restart`  执行network服务中的start命令，开启network服务


参考：[Linux命令中service的用法](https://www.cnblogs.com/wuheng1991/p/7064067.html)

# chkconfig

## 简介

chkconfig是管理系统服务(service)的命令行工具。所谓系统服务(service)，就是随系统启动而启动，随系统关闭而关闭的程序。
chkconfig可以更新(启动或停止)和查询系统服务(service)运行级信息。更简单一点，chkconfig是一个用于维护/etc/rc[0-6].d目录的命令行工具。

## 使用范例
* `chkconfig --list`      列出所有的系统服务
* `chkconfig --add httpd` 增加httpd服务
* `chkconfig --del httpd` 删除httpd服务
* `chkconfig --level 345 httpd on` 把httpd在运行级别为3、4、5的情况下都是on（开启）的状态。
* `chkconfig httpd on` --level不指定时,httpd的运行级别默认为2、3、4、5

参考：[Linux的运行级别和chkconfig用法](https://www.cnblogs.com/terryguan/p/4551012.html)

# ntsysv

ntsysv：类图形界面管理模式来设置开机启动。（RedHat特有的，基本上chkconfig就很好用了。）

# systemctl

## 简介

systemctl命令是系统服务管理器指令，主要负责控制systemd系统和服务管理器，它实际上将 service 和 chkconfig 这两个命令组合到一起。

CentOS 7.x开始，CentOS开始使用systemd服务来代替daemon，原来管理系统启动和管理系统服务的相关命令全部由systemctl命令来代替。

## 如何编写service文件

http://www.jinbuguo.com/systemd/systemd.service.html#
http://www.jinbuguo.com/systemd/systemd.unit.html

参考：[linux命令学习之:systemctl - kosamino - 博客园](https://www.cnblogs.com/jing99/p/7895860.html)
