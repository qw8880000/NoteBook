问题现象：win10一直连不上ubuntu的smb服务

排查方法：

找开"计算机管理"->"应用程序和服务日志"->"Microsoft"->"Windows"->"SMBClient"->"Connectivity"
![image](http://qiniu.wangjinle.com/smb_win10_1.png)

打开错误信息
![image](http://qiniu.wangjinle.com/smb_win10_2.png)

可以看到win10的smb client客户端一直使用445端口去连接我的smb服务，可是我的smb服务的监听端口是139，于是就连接失败了。

既然知道原因就好解决了，把smb的监听端口改成445，或者修改win10 smb client所使用的端口为139。

