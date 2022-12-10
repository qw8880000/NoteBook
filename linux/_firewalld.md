- [CentOS 上的 FirewallD 简明指南](https://linux.cn/article-8098-1.html)

# 起停
1.  启动服务 `systemctl start firewalld`
1.  停止服务 `systemctl stop firewalld`
2.  查看服务状态 `systemctl status firewalld`
3.  重新加载firewalld配置 `firewall-cmd --reload`


# 配置

FirewallD 使用两个配置集：“运行时”和“持久”。 在系统重新启动或重新启动 FirewallD 时，不会保留运行时的配置更改，而对持久配置集的更改不会应用于正在运行的系统。
默认情况下，firewall-cmd 命令适用于运行时配置，但使用 --permanent 标志将保存到持久配置中。要添加和激活持久性规则，你可以使用两种方法之一

1、 将规则同时添加到持久规则集和运行时规则集中。
```
    firewall-cmd --zone=public --add-service=http --permanent
    firewall-cmd --zone=public --add-service=http
```

2、 将规则添加到持久规则集中并重新加载 FirewallD。
```
firewall-cmd --zone=public --add-service=http --permanent
firewall-cmd --reload
```

# 丰富规则

丰富规则的语法有很多，但都完整地记录在 firewalld.richlanguage(5) 的手册页中（或在终端中 man firewalld.richlanguage）。 使用 --add-rich-rule、--list-rich-rules 、 --remove-rich-rule 和 firewall-cmd 命令来管理它们。

这里有一些常见的例子：
允许来自主机 192.168.0.14 的所有 IPv4 流量：
```
firewall-cmd --zone=public --add-rich-rule 'rule family="ipv4" source address=192.168.0.14 accept'
```

拒绝来自主机 192.168.1.10 到 22 端口的 IPv4 的 TCP 流量。
```
firewall-cmd --zone=public --add-rich-rule 'rule family="ipv4" source address="192.168.1.10" port port=22 protocol=tcp reject'
```

列出你目前的丰富规则：
```
firewall-cmd --list-rich-rules
```

# 常用命令

- 查看指定接口所属区域：`firewall-cmd --get-zone-of-interface=eth0`
- 查看当前zone的规则：`firewall-cmd --list-all`