---
title: 蓝牙核心框架 | bluetooth
date: 2017-10-27 17:52:43
categories:
    - bluetooth
tags:
    - bluetooth
abbrlink: @@abbrlink
---
## Bluetooth core system architecture

蓝牙核心系统由一个 Host，一个Primary Controller 和0个或多个Secondary Controllers组成。

![image](http://www.wowotech.net.img.800cdn.com/content/uploadfile/201601/6dc67a1dce48e839916bd974208a7fea20160114142023.gif)

Link Manager, Link Controller and BR/EDR Radio blocks comprise a **BR/EDR Controller**.  
An AMP PAL, AMP MAC, and AMP PHY comprise an **AMP Controller**.  
Link Manager, Link Controller and LE Radio blocks comprise an **LE Controller**.  
L2CAP, SDP and GAP blocks comprise a **BR/EDR Host**.  
L2CAP, SMP, Attribute protocol, GAP and Generic Attribute Profile (GATT) blocks comprise an **LE Host**.  
A BR/EDR/LE Host combines the set of blocks from each respective Host.  

蓝牙核心协议有：
* Radio (PHY) protocol
* Link Control (LC) and Link Manager (LM) protocol or Link Layer (LL) protocol
* AMP PAL
* Logical Link Control and Adaptation protocol (L2CAP)
* AMP Manager Protocol

另外，Service Discovery Protocol (SDP)和Attribute Protocol (ATT)是应用层协议。


## CORE ARCHITECTURAL BLOCKS

### Host Architectural Blocks

BR/EDR and LE 体系有一部分是共用，有一部分是各自实现。

* Channel Manager  
* L2CAP Resource Manager  
* Security Manager Protocol  
* Attribute Protocol  
* AMP Manager Protocol  
* Generic Attribute Profile  
    GATT is used on LE devices for LE profile service discovery.
* Generic Access Profile  

### BR/EDR/LE Controller Architectural Blocks

BR/EDR and LE 体系有一部分是共用，有一部分是各自实现。

* Device Manager  
* Link Manager  
    Link Manager Protocol (LMP) in BR/EDR and the Link Layer Protocol (LL) in LE
* Baseband Resource Manager  
* Link Controller  
* PHY  

### AMP Controller architectural blocks

* AMP HCI
* AMP PAL
* AMP MAC
* AMP PHY
