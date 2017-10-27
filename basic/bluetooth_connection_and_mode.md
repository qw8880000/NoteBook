---
title: 连接和模式 | bluetooth
date: 2017-10-27 17:53:30
categories:
    - bluetooth
tags:
    - bluetooth
abbrlink: @@abbrlink
---

## OPERATIONAL PROCEDURES AND MODES

蓝牙操作最常见的就是设备相互连接并交换数据。

### BR/EDR 操作

#### Inquiry (Discovering) 操作

一个尝试对外搜索设备的设备，称为inquiring device.
它向外发送查询请求(inquiry requests).

一个可被发现的设备，称为discoverable device.
它监听查询请求，并发送响应(inquiry response)。

有一种扩展响应包(Extended Inquiry Response)，它可以包含各种信息如：设备名称，支持的服务，信息和其他。
这样可以缩短接收响应的设备获得有用信息的时间。
Extended Inquiry Response 兼容 standard inquiry response。

#### Paging (Connecting) 操作

这个操作用来在两个设备间形成连接。
设备发起连接，另一方响应连接。
发起连接的一方叫paging device，响应连接的一方叫connectable device。

### BR/EDR mode 

#### Connected Mode
// to do 
#### Hold Mode
// to do 
#### Sniff Mode
// to do 
#### Parked State
// to do 
#### Connectionless Slave Broadcast Mode
// to do 

### LE 操作

#### Device Filtering
// to do 
#### Advertising

advertising device使用advertising操作向外发送无连接的广播数据。
advertising操作用来与附近的initiating devices建立连接，或者向scanning devices 提供周期性的用户数据广播包。
advertising操作使用advertising physical channel。

advertising device 有可能会收到其他设备请求用户数据的scan requests。
advertising device 使用同一物理信道进行响应。

advertising device 会在advertising broadcast physical channel收到initiator devices发送过来的连接请求(connection requests)。

#### Scanning

scanning device 使用scanning操作在advertising physical channel监听从advertising devices过来的无连接的用户数据广播包。
scanning device 可以在advertising physical channel 上向advertising device请求更多的用户数据。

当scanning device收到connectable advertising events，并且它处于initiator mode，
那么它可以发起一个连接。一旦连接发出，那么它从initiator mode进入到connected mode。


