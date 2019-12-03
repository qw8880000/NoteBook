先说明一下我的环境：VMware Workstation 15 上安装的ubuntu，ubuntu上安装了mysql 5.7.25版本，监听端口是3306。

出现的问题现象是我的宿主机windows死活telnet不通虚拟机上的3306端口，但是可以telnet通22端口。

可以连通22端口说明主机与虚拟机之前的网络没问题，于是想到可能是防火墙问题，关闭防火墙问题后还是不行。

查看netstat -lntp，发现mysql的监听地址是127.0.0.0：
![image](http://qiniu.wangjinle.com/telnet3306_netstat.png)

于是修改mysql.cnf，把bind-address改成0.0.0.0：
![image](http://qiniu.wangjinle.com/telnet3306_netstat.png)

重启mysql后，问题解决。

这里有一个知识点是127.0.0.0 地址与 0.0.0.0地址的区别，有兴趣的同学可以去了解一下。



