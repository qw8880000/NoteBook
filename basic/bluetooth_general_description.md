---
title: 蓝牙简介 | bluetooth
date: 2017-10-27 17:49:14
categories:
    - bluetooth
tags:
    - bluetooth
abbrlink: babe1bcba164dc7d
---

## 简介

有两种蓝牙技术体系：Basic Rate (BR) 和 Low Energy (LE)。
两种体系都包括 设备搜索，建立连接，连接管理。

Basic Rate(BR)技术体系为以下3种技术提供同步和异步的连接：
* 数据传输率为 721.2 kb/s 的 **Basic Rate**
* 数据传输率为 2.1 Mb/s 的 **Enhanced Data Rate**
* 数据传输率为 54 Mb/s 的 802.11 **AMP**

Low Energy(LE)技术体系相比BR技术具有低功耗，低复杂度，开支小，低速率等特点。

实现了两种技术体系的设备可以和实现了两种技术体系的设备通信，也可以和只实现了其中一种体系的设备通信。
但是只实现一种技术体系的设备无法跟只实现另外一种技术体系的设备通信。
一些规范和使用方式只有其中一种技术体系支持；如果一个设备实现了两种技术体系，
那么它可以支持几乎所有的规范和使用方式。

蓝牙核心系统(Bluetooth Core system)由 一个 **Host** 和 一个或多个 **Controller** 组成。

![image](http://oxnimkw03.bkt.clouddn.com/8ef568eb90bdb6aa4e9cff885734fe2620140523101501.gif)

Host 指规范(profiles)以下 **HCI**(Host Controller Interface)以上的各层组成的逻辑实体。
Controller 指 HCI以下各层组成的逻辑实体。

Controller 包括：主控制器(Primary Controllers)和次控制器(Secondary Controllers)。

只实现主控制器的蓝牙核心有以下3种配置：
* BR/EDR Controller，包含： Radio, Baseband, Link Manager and optionally HCI
* LE Controller，包含：LE PHY, Link Layer and optionally HCI
* 集成BR/EDR Controller 和 LE Controller 到一个控制器里，并共用MAC地址。

包含主控制器和次控制器的蓝牙核心有：
* an Alternate MAC/PHY (AMP) Controller including an 802.11 PAL (Protocol Adaptation Layer), 802.11 MAC and PHY, and optionally HCI。

![image](http://oxnimkw03.bkt.clouddn.com/bluetooth_host_and_controller.jpg)
![image](http://oxnimkw03.bkt.clouddn.com/bluetooth_host_and_controller2.jpg)

