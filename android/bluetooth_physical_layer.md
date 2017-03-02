
## 蓝牙物理层( Bluetooth physical layer )

```
Bluetooth physical layer consists of baseband and radio specifications as defined in IEEE 802.15.1.
```

蓝牙物理层由基带和射频规范组成。

## 跳频 ( Frequency hopping )

```
It serves two purpose, one is that it helps provide resistance to multipath interference. Second one is that it provide multiple access to devices in different piconets co-located.
```

跳频的作用：
* 防止多路径干扰
* 设备在不同的piconet中提供不同的访问通路

## 物理连接 ( Physical links )

master与slave之间可以建立以下两种连接：
* SCO  
    `Synchronous connection oriented`，有调整的同步连接，master与slave之间使用固定带宽
* ACL
    `Asynchronous connectionless`，异步无连接，

## 基带包格式 ( Baseband packet formats )

```
Bluetooth Packet Format = Access Code(72 bits) + Header(54 bits) + Payload (0 to 2745 bits) 
Access code consists of preamble(4bits),sync word(64bits) and trailer field(4 bits).
Header field consists of AM_ADDR(3 bits), type(4 bits),flow(1 bit),ARQN(1 bit),SEQN(1 bit) and HEC(8 bits).
```

## 纠错方法(  Error Correction Methods )

```
1/3 rate forward error correction (FEC) 
2/3 rate forward error correction (FEC)
Automatic Repeat Request Scheme (ARQ)
```

