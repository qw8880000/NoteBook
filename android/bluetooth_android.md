
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

