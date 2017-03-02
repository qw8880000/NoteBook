
## 蓝牙MAC层( Bluetooth MAC layer )

```
Bluetooth MAC layer consists of Link Manager Protocol(LMP) and Logical Link Control and Adaptation Protocol(L2CAP).
```
蓝牙MAC层( Bluetooth MAC layer )的组成：
* Link Manager Protocol(LMP) 
* Logical Link Control
* Adaptation Protocol(L2CAP)

## 逻辑通道( Logical channels )

```
Bluetooth standard defines five different types of logical data channels based on different payload traffic carried by them. 
They are link control, link manager,user asynchronous,user isochronous and user synchronous
```

## Link Manager Protocol(LMP)

```
LMP protocol is used to establish the link and to control the link. 
Link Control (LC) provides the reliability to Link Manager Protocol. 
LM PDUs are sent in single slot packets.
PDU = Opcode(7bits), transaction ID(1bit), information contents
```

## Logical Link Control and Adaptation Protocol(L2CAP)

```
This L2CAP protocol like LLC takes care of link layer protocol services between the entities. 
It provides services to upper layers and rely on lower layer for flow control as well as error control.
L2CAP makes use of ACL links and does not use SCO links.

L2CAP provides two type of services connectionless and connection mode services. 
Connectionless type provide reliable datagram delivery service. 
Connection mode type provide service using HDLC protocol.
```

# 参考

* [Bluetooth MAC layer](http://www.rfwireless-world.com/Tutorials/Bluetooth-MAC-layer.html)

