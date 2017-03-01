
## Bluetooth Work Model

蓝牙有两种工作模式：
* Master (主设备)
* Slave (从设备)

```
a single master device can be connected to up to seven different slave devices. 
Any slave device in the piconet can only be connected to a single master
```
一个主设备最多能连接7个从设备，而一个从设备只能连接一个主设备.

## Bluetooth Network

![Bluetooth-Network-Topologies](http://www.rfwireless-world.com/images/Bluetooth-Network-Topologies.jpg)

```
Bluetooth network consists of many bluetooth users. 
There are two types of network topologies in bluetooth viz.  Piconet and scatternet
```
蓝牙的网络分两种：
* piconet(微微网)
* scatternet(散射网)

### piconet

![piconet](https://upload.wikimedia.org/wikipedia/commons/thumb/8/81/BluetoothPiconet-de.svg/304px-BluetoothPiconet-de.svg.png)

```
Piconet is formed by one master and one slave as well as one master and multiple slaves. 
There will be maximum 7 active slaves in the piconet.
There will be about 255 slaves in parking state.
Slaves are not allowed to talk to each other directly.  All communication occurs within the slave and the master.
Slaves within a piconet must also synchronize their internal clocks and frequency hops with that of the master.
```
Piconet:
* 由1个master(主设备)和多个slave(从设备)组成.
* 其中活动的从设备最多只能是7个。
* 非活动状态的从设备可以最多有255个。
* slaves 之间无法直接通信.所有的通信都是发生在master 与 slave之间.
* slaves会与piconet中的master同步时钟可频率

### scatternet

![scatternet](https://encrypted-tbn2.gstatic.com/images?q=tbn:ANd9GcSohnGRLnuHn381Odn93zH67tNBqmBXfewGxL_3fm-yhWZA4OLAwA)

```
Combinations of multiple piconets is known as scatternet.
Each piconet uses a different frequency hopping sequence.
```

scatternet:
* 多个piconets组成scatternet
* 不同的piconet工作在不同的频率


![ms](https://encrypted-tbn2.gstatic.com/images?q=tbn:ANd9GcRraH-ngnaKKdP0HZ8RC1SxEnS6TlUbY9tML3td_vpfFz44tzNYmw)

```
A device can participate in multiple piconets.
Radio devices used Time Division Multiplexing (TDM). 
A master device in a piconet transmits on even numbered slots and the slaves may transmit on odd numbered slots.
Each piconet may have only one master, but slaves may participate in different piconets on a time-division multiplex basis. 
A device may be a master in one piconet and a slave in another or a slave in more than one piconet.
```

* 分时，master使用偶数时间片，slave使用奇数时间片
* 一个设备可以参与多个piconets
* 一个设备在某个piconet中可能是slave角色，在另一个piconet中可能是master角色.
* 也就是说一个设备可能即是slave又是master.


## 参考

* [Bluetooth Basics](http://sna.csie.ndhu.edu.tw/~cnyang/PDF/bt_tut.pdf)
* [Bluetooth Tutorial](http://www.rfwireless-world.com/Tutorials/Bluetooth_tutorial.html)
* [Bluetooth Tutorial](http://www.tutorial-reports.com/wireless/bluetooth/tutorial.php)
* [Bluetooth Basics](https://learn.sparkfun.com/tutorials/bluetooth-basics)

