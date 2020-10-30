## 修改最大打开文件数、最大进程数

修改/etc/security/limits.conf配置：
```
* soft    nofile           65535
* hard    nofile           65535
* soft nproc 2048
* hard nproc 4096 
```

centos7 systemd服务 设置/etc/security/limits.conf不起作用，需要配置/etc/systemd/system.conf
```
DefaultLimitCORE=infinity
DefaultLimitNOFILE=100000
DefaultLimitNPROC=100000
```

vi /etc/security/limits.d/90-nproc.conf
* soft nofile 65536
* hard nofile 131072
* soft nproc 2048
* hard nproc 4096 

https://www.cnblogs.com/chris-cp/p/6667753.html
