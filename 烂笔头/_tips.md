# 多个JAVA版本切换

安装jdk版本到系统中
alternatives --install /usr/bin/java java /home/apps/jdk1_8_112/bin/java 2

指定默认的jdk版本
alternatives --config java

# telnet

为了验证一台设备的某个端口是否可连接，一般都会使用telnet命令。我猜测telnet命令的基本原理是使用socket套接字，尝试去连接某设备的端口。

# 收藏

  - [Linux里的2>&1究竟是什么，这篇文章告诉你](https://mp.weixin.qq.com/s/AXvohWzCAV6iabl2p652tw)
