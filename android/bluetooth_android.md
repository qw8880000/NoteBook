
[1]: https://developer.android.com/guide/topics/connectivity/bluetooth.html?hl=zh-cn "API Guides"
[2]: https://developer.android.com/guide/topics/connectivity/bluetooth.html "Classic Bluetooth"
[3]: https://developer.android.com/guide/topics/connectivity/bluetooth-le.html#terms "Bluetooth Low Energy"

## 蓝牙

蓝牙可分为两种：[ Classic Bluetooth ][2] 与 [ Bluetooth Low Energy ][3]

## Bluetooth Low Energy

Android 4.3 (API level 18) 以上 才支持BLE

### BLE关键术语和概念

* [Bluetooth Low Energy]( https://developer.android.com/guide/topics/connectivity/bluetooth-le.html#terms ) 
* [Android Bluetooth Low Energy（Android低功耗蓝牙）](http://blog.csdn.net/qinxiandiqi/article/details/40741269)

## android 的蓝牙协议栈

* Bluez
* Bluedroid

## 蓝牙开发

### 搜索蓝牙设备

`BluetoothAdapter`类
* `startDiscovery()`   
    搜索所有蓝牙设备
* `startLeScan()`  
    只搜索BLE bluetooth

### 设置蓝牙可见性

`BluetoothAdapter.ACTION_REQUEST_DISCOVERABLE`

### android 手机 创建 GATT server

* [qw8880000/android-samples](https://github.com/qw8880000/android-samples) 中的 `BluetoothGatt`

### android advertise

如何使android设备发送广播包，参考
* [qw8880000/android-samples](https://github.com/qw8880000/android-samples) 中的 `BluetoothScanner`

收与发，参考
* [googlesamples/android-BluetoothAdvertisements](https://github.com/googlesamples/android-BluetoothAdvertisements)

## 问题

### 手机与手机是如何连接

首先肯定是一方作为服务器端，一边作为客户端。

服务器端
1. 调用 `listenUsingRfcommWithServiceRecord(String, UUID)`得到一个 `BluetoothServerSocket`；
1. 然后通过调用`accept()`开始侦听连接请求。

客户端
1. 使用 `BluetoothDevice`,通过调用 `createRfcommSocketToServiceRecord(UUID)`到一个 `BluetoothSocket`
1. 调用 `connect()`初始化连接

两边的 UUID 必须是一样的，这是一个服务的唯一标识，而且这个 UUID 的值必须是 `00001101-0000-1000-8000-00805F9B34FB`。
为什么呢？因为这个是 Android 的 API 上面说明的，用于普通蓝牙适配器和 Android 手机蓝牙模块连接的。

### 为什么发送advertise包，device address地址不是蓝牙的地址

安卓5后，android 的 Bluetooth api增加了 `BluetoothLeAdvertiser` 接口用来发送广播包。
其中有一个保护隐私的特性就是：广播包的device address每隔一段时间就会改变一次。

这是为了安全考虑，其他人无法通过device address来追踪你的蓝牙设备。


参考：
* [Android 5 static bluetooth MAC address for BLE advertising](http://stackoverflow.com/questions/28602672/android-5-static-bluetooth-mac-address-for-ble-advertising)
* [Why the address of my BluetoothDevice changes every time I relaunch the app?](http://stackoverflow.com/questions/36180407/why-the-address-of-my-bluetoothdevice-changes-every-time-i-relaunch-the-app)

## 参考

* [bluetooth api guides](https://developer.android.google.cn/guide/topics/connectivity/bluetooth.html?hl=zh-cn)
* [Bluetooth Low Energy](https://developer.android.google.cn/guide/topics/connectivity/bluetooth-le.html?hl=zh-cn)
* [Bluetooth guide](https://developer.android.com/guide/topics/connectivity/bluetooth.html)
* [Bluetooth guide - 中文](http://www.jianshu.com/p/fc46c154eb77)
* [googlesamples/android-BluetoothChat](https://github.com/googlesamples/android-BluetoothChat)
* [googlesamples/android-BluetoothLeGatt](https://github.com/googlesamples/android-BluetoothLeGatt)
* [googlesamples/android-BluetoothAdvertisements](https://github.com/googlesamples/android-BluetoothAdvertisements)

