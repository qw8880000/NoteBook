现象：secureCRT在ssh连接ubuntu时特别慢。可能原因为：DNS解析IP导致.

解决办法：

1. 在ssh服务端上更改/etc/ssh/sshd_config 文件中的配置增加：`UseDNS no`
1. 重启ssh服务: /etc/init.d/ssh restart