
[1]: https://developer.android.com/guide/topics/connectivity/bluetooth.html?hl=zh-cn "API Guides"
[2]: https://developer.android.com/guide/topics/connectivity/bluetooth.html "Classic Bluetooth"
[3]: https://developer.android.com/guide/topics/connectivity/bluetooth-le.html#terms "Bluetooth Low Energy"

## 蓝牙

蓝牙可分为两种：[ Classic Bluetooth ][2] 与 [ Bluetooth Low Energy ][3]

## Bluetooth Low Energy

Android 4.3 (API level 18) 才支持BLE

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

* [ble-android-gatt-server/BluetoothLeService.java](https://github.com/jeffddrake/ble-android-gatt-server/blob/master/BluetoothLeGattSample/src/main/java/com/example/android/bluetoothlegatt/BluetoothLeService.java)
* [PeripheralActivity.java - GitHub]( https://github.com/devunwired/accessory-samples/blob/master/BluetoothGattPeripheral/src/main/java/com/example/android/bluetoothgattperipheral/PeripheralActivity.java )
* [Android as Bluetooth Low Energy Peripheral (GATT server).]( http://blog.csdn.net/u013606170/article/details/46038283 )

### android advertise

* [AdvertiserActivity.java - Github](https://github.com/devunwired/accessory-samples/blob/master/bluetoothadvertiser/src/main/java/com/example/android/bluetoothadvertiser/AdvertiserActivity.java)

### 手机与手机是如何配对

首先肯定是一方作为服务器端，一边作为客户端。

服务器端
1. 调用 `listenUsingRfcommWithServiceRecord(String, UUID)`得到一个 `BluetoothServerSocket`；
1. 然后通过调用`accept()`开始侦听连接请求。

客户端
1. 使用 `BluetoothDevice`,通过调用 `createRfcommSocketToServiceRecord(UUID)`到一个 `BluetoothSocket`
1. 调用 `connect()`初始化连接

两边的 UUID 必须是一样的，这是一个服务的唯一标识，而且这个 UUID 的值必须是 `00001101-0000-1000-8000-00805F9B34FB`。
为什么呢？因为这个是 Android 的 API 上面说明的，用于普通蓝牙适配器和 Android 手机蓝牙模块连接的。

## 参考

* [bluetooth api guides](https://developer.android.google.cn/guide/topics/connectivity/bluetooth.html?hl=zh-cn)
* [Bluetooth guide](https://developer.android.com/guide/topics/connectivity/bluetooth.html)
* [Bluetooth Low Energy](https://developer.android.google.cn/guide/topics/connectivity/bluetooth-le.html?hl=zh-cn)
* [BluetoothAdapter](https://developer.android.com/reference/android/bluetooth/BluetoothAdapter.html)
* [Android经典蓝牙开发简介](http://www.jianshu.com/p/fc46c154eb77)
* [Android蓝牙实例（和单片机蓝牙模块通信）](http://www.cnblogs.com/luoxn28/p/5440882.html)

