
## BR/EDR 简介

Basic Rate / Enhanced Data Rate (BR/EDR) 射频工作在 2.4 GHz 的 ISM 频段。

物理射频层的典型的操作是，一组设备工作在相同的时钟(**clock**)和跳频模式(**frequency hopping pattern**)。
其中，提供同步参照物的设备叫主设备(**Master**)。
其他设备去同步master的时钟和跳频模式，这些设备叫从设备(**Slave**).
这样一组设备组成一个微微网(**piconet**).
这是BR/EDR技术中设备通信的基础。

![piconet](https://upload.wikimedia.org/wikipedia/commons/thumb/8/81/BluetoothPiconet-de.svg/304px-BluetoothPiconet-de.svg.png)

微微网中的设备使用一个特定的跳频模式，该算法通过主设备的蓝牙地址和时钟频率来确定。
基本跳频模式是一个伪随机序，有79个频率，被1MHz相分离，在ISM频段。
跳频模式用于抗干扰，并提高与非跳频的蓝牙共存。

物理信道(**physical channel**)被划分成时间单元，称为时隙(slot).
蓝牙设备的数据被放在这些时隙中传输。

在物理信道上面有一个分层的链接，通道和相关控制协议.
层次是：
* 物理信道(physical channel)
* 物理链路(physical link)
* 逻辑传输(logical transport)
* 逻辑链路(logical link)
* L2CAP信道(L2CAP channel).

在物理信道之上，主设备和从设备之间形成物理链路(**physical link**)。
然而，Inquiry scan 和 Page scan 的物理通道并没有相关联的物理链路。
物理链路提供在主设备和从设备间的双向数据包传输功能，除非是无连接的从设备物理链路。
这种情况下，物理链路为主设备提供单向数据传输能力。
在一个微微网中，从设备之间不允许形成物理链路，物理链路只允许在主设备和从设备之间形成。
这就意味着，从设备之间无法直接通信，只能是主设备与从设备的通信。

逻辑链路(**logical link**)基于物理链路。
一个物理链路将会被一个或多个逻辑链路使用。

链路控制协议，link manager protocol (**LMP**).
LMP基于逻辑链路，用来控制基带层(baseband)和物理层(physical layers).
微微网中的活跃设备(active devices)有默认的面向连接的异步逻辑链路，用来传输LMP协议信号。
由于历史原因，这叫做**ACL**逻辑链路。
对于无连接的从模式广播设备(Connectionless Slave Broadcast devices)，ACL逻辑链路是不需要的。

链路管理器(The Link Manager function) 使用LMP控制设备的行为，并提供服务用来管理底层(radio layer and baseband layer).
The LMP protocol is only carried on the primary ACL logical transport and the default broadcast logical transport

**L2CAP**，在基带层之上，为应用和服务提供基于通道的抽象(channel-based abstraction).
它执行应用数据的分割和重组以及通过共享逻辑链路(logical link)对多个信道(channels)的复用和解复用.

![image](http://www.rfwireless-world.com/images/bluetooth-protocol-stack.jpg)

