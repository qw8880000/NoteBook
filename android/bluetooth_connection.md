
## 蓝牙之间的连接

蓝牙之间的连接分为3个过程：

1. **Inquiry**  
    如果两个设备互相不知道对方，那么必需有一方工作在查询模式。
    这个设备会不停的发送查询命令，接下来附近的设备回复一个响应，这个响应包含它的地址、名称、其他信息.
1. **Paging (Connecting)**   
    这个过程中，两个设备需要同步时钟与频率，还有一些其他的。
1. **Connection**  
    上一步之后两个设备进入连接状态。当连接上后，设备可以选择进入休眠模式，或者保持活动状态。

## 蓝牙工作模式

* *Active Mode*  
    这是最平常的模式，设备处于活动状态，正常收发数据。
* *Sniff Mode*  
    这是一种节能模式，设备处于休眠并每隔一段时间唤醒一次
* *Hold Mode*  
    这是一种临时休眠模式，设备会休眠一段指定的时间然后唤醒，并一直处于活动状态。
    主设备可以命令从设备进入`hold mode`
* *Park Mode*  
    这是一种深度休眠模式，主设备可以命令一个从设备进入此模式，从设备休眠直到主设备命令它唤醒。

## 参考

* [Bluetooth Basics](https://learn.sparkfun.com/tutorials/bluetooth-basics)
* [Establishing Connections in Bluetooth](http://www.tutorial-reports.com/wireless/bluetooth/establishingconnections.php)
