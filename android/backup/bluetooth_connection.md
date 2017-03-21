

## 蓝牙之间的连接

蓝牙之间的连接分为3个过程：

1. **Inquiry**  
    如果两个设备互相不知道对方，那么必需有一方工作在查询模式。
    这个设备会不停的发送查询命令，接下来附近的设备回复一个响应，这个响应包含它的地址、名称、其他信息.
1. **Paging (Connecting)**   
    这个过程中，两个设备需要同步时钟与频率，还有一些其他的。
1. **Connection**  
    上一步之后两个设备进入连接状态。当连接上后，设备可以选择进入休眠模式，或者保持活动状态。

## Inquiry

### Inquiry scan (slave)

An unconnected Bluetooth device that wants to be "discovered" by a master device will periodically enter the inquiry scan state; 

in this state, the device activates its receiver and listens for inquiries. 

It must enter this state at least every 2.56 seconds (4096 slots).

During the inquiry scan state, the unconnected device listens on one of 32 channels, for at least 10ms (16 slots). 

A different channel is selected every 1.28 seconds (2048 slots). 

The channels and the hopping sequence are calculated from the general inquiry address.

### Inquiry (master)

When commanded to enter the inquiry state, the master device starts to transmit, 
using 16 of the 32 channels used for inquiries. 

During every even numbered slot it transmits two ID packets on two different channels, 
and during the following slot it listens on those two channels for a slave's response (an FHS packet). 

In the next two slots it uses the next two channels, so the hopping sequence (of 16 channels) repeats every 10ms (16 slots). 

The 16 slot sequence must be repeated at least 256 times (i.e. for at least 2.56 seconds) before 
switching to the other set of 16 channels.

参考：http://www.dziwior.org/Bluetooth/Inquiry.html

## 蓝牙之间的绑定

绑定需要建立在连接之上，即两个蓝牙需要互相发现，建立连接，然后才能绑定。

## 参考

* [Bluetooth Basics](https://learn.sparkfun.com/tutorials/bluetooth-basics)
* [Establishing Connections in Bluetooth](http://www.tutorial-reports.com/wireless/bluetooth/establishingconnections.php)

