
## LE 简介

Like the BR/EDR radio, the LE radio operates in the unlicensed 2.4 GHz ISM band.

LE系统采用跳频收发器来抵抗干扰和衰落，并提供许多FHSS载波。

LE采用两种多址方案:Frequency division multiple access (FDMA) and time division multiple access (TDMA)
FDMA方案有40个物理信道，每个信道由2MHz隔离。其中3个是广播信道(advertising channels)，37个是数据信道(data channels).
TDMA方案，设备在预定时间发送数据包，相应的设备在预定的间隔之后回应数据包。

物理信道(physical channel)被细分为称为事件(**events**)的时间单位。
设备之间把数据包放在事件中传输。
有两种事件：**Advertising** and **Connection** events

在广播物理信道(advertising PHY channels)上发送广播包(advertising packets)的设备称为**advertisers**.
在广播信道上接收广播包的设备称**scanners**.

scanner 在收到 advertising packet 后，可以在同一物理广播信道上发送请求。
Advertiser 使用同一物理广播信道回复数据。
