# docker 部署

zabbix agent
```
docker run --name some-zabbix-agent -e ZBX_HOSTNAME="some-hostname" -e ZBX_SERVER_HOST="some-zabbix-server" -p 10050:10050 -d zabbix/zabbix-agent:tag
```

# 资料
  - [Zabbix Documentation 3.4 - 中文](https://www.zabbix.com/documentation/3.4/zh/manual) 官方文档
