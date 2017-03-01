
## 蓝牙之间的连接

蓝牙之间的连接分为3个过程：

1. **Inquiry**  
    如果两个设备互相不知道对方，那么必需有一方工作在查询模式。
    这个设备会不停的发送查询命令，接下来附近的设备回复一个响应，这个响应包含它的地址、名称、其他信息.
1. **Paging (Connecting)**   
    这个过程中，两个设备需要同步时钟与频率，还有一些其他的。
1. **Connection**  
    上一步之后两个设备进入连接状态。当连接上后，设备可以选择进入休眠模式，或者保持活动状态。


## 参考

* [Bluetooth Basics](https://learn.sparkfun.com/tutorials/bluetooth-basics)
* [Establishing Connections in Bluetooth](http://www.tutorial-reports.com/wireless/bluetooth/establishingconnections.php)
