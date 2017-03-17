## 低耗电蓝牙BLE（Bluetooth Low Energy）

Bluetooth low energy (Bluetooth LE, BLE, marketed as Bluetooth Smart) 

BLE是在蓝牙4.0的核心规范中引入的。

BLE是标准的蓝牙（协议规范）的一个轻量级的子集

4.0以前的蓝牙，控制器和主机是分开的，而BLE中控制器和主机是在一起的。

BLE的相对于标准蓝牙的一些主要特点：
* 低成本
* 短距离
* 超低功耗(ULP)

## BLE 芯片

BLE的芯片实现有两种模式：

* 单模 - BLE
    * 只实现了BLE
* 双模 - Bluetooth Classic+BLE
    * 将Bluetooth Smart即BLE集成到已有的经典的蓝牙协议中

## BLE 的角色

In BLE, there is a distinction between the concepts **Central/Peripheral** and **Server/Client**:

* Central/Peripheral is relating to the network architecture, 
    where the central is the hub in a star, with one or more peripherals connected to it. 
    It will typically be a phone, tablet or computer. 
    A peripheral device can only connect to one central at a time.
* Server/Client (GATT server/client) is a higher level concept, 
    related to the data that are kept in the devices and possibly communicated over the connection. 
    Both central and peripheral devices can implement a GATT server and a GATT client, 
    but is not required to have both.

## How does BLE communication work

BLE communication consists of two main parts: **advertising** and **connecting**.

#### advertising

Advertising is a one-way discovery mechanism.

Devices which want to be discovered can transmit packets of data in intervals from 20 ms to 10 seconds. 

The shorter the interval, the shorter the battery life, but the faster the device can be discovered.

The packets can be up to 47 bytes in length and consist of:

* 1 byte preamble
* 4 byte access address
* 2-39 bytes advertising channel PDU
* 3 bytes CRC

![iamge](http://www.warski.org/blog/wp-content/uploads/2014/01/bluetooth-le-packet-300x121.png)

BLE devices can operate in a non-connectable advertisement-only mode (where all the information is contained in the advertisement), but they can also allow connections (and usually do).

#### connecting

After a device is discovered, a connection can be established. 

It is then possible to read the services that a BLE device offers, 
and for each service its characteristics (this is also known as an implementation of a GATT profile). 

Each characteristic provides some value, which can be read, written, or both. 

For example a smart thermostat can expose one service for getting the current 
temperature/humidity readings (as characteristics of that service) and another 
service and characteristic to set the desired temperature. 

参考：
* [How do iBeacons work?](http://www.warski.org/blog/2014/01/how-ibeacons-work/)
