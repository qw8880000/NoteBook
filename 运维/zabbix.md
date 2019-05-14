# docker 部署

zabbix agent
```
docker run --name some-zabbix-agent -e ZBX_HOSTNAME="some-hostname" -e ZBX_SERVER_HOST="some-zabbix-server" -p 10050:10050 -d zabbix/zabbix-agent:tag
```

# zabbix 监牢主机到外网IP的连通性

监控项 -> 简单检查 -> icmpping

icmpping[<target>,<packets>,<interval>,<size>,<timeout>]说明：
https://www.zabbix.com/documentation/3.4/zh/manual/config/items/itemtypes/simple_checks

# zabbix agent suse系统安装

增加zabbix用户与用户组
1. groupadd zabbix
1. useradd -g zabbix zabbix

编译部分
1. ./configure --enable-agent
2. make install

设置服务与开机启动
3. cp zabbix-3.4.6/misc/init.d/suse/9.3/zabbix_agentd /etc/init.d/
4. chmod +x /etc/init.d/zabbix_agentd
5. chkconfig --add zabbix_agentd
6. chkconfig zabbix_agentd on

配置/usr/local/etc/zabbix_agentd.conf
```
Server=192.168.1.5
ServerActive=192.168.1.5
Hostname=192.20.103.90
```

# 资料
  - [Zabbix Documentation 3.4 - 中文](https://www.zabbix.com/documentation/3.4/zh/manual) 官方文档
  - 《Zabbix监控系统深度实践》
