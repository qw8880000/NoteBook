
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

## 参考

* [bluetooth api guides](https://developer.android.google.cn/guide/topics/connectivity/bluetooth.html?hl=zh-cn)
* [Bluetooth guide](https://developer.android.com/guide/topics/connectivity/bluetooth.html)
* [Bluetooth Low Energy](https://developer.android.google.cn/guide/topics/connectivity/bluetooth-le.html?hl=zh-cn)
* [BluetoothAdapter](https://developer.android.com/reference/android/bluetooth/BluetoothAdapter.html)
* [Android经典蓝牙开发简介](http://www.jianshu.com/p/fc46c154eb77)
* [Android蓝牙实例（和单片机蓝牙模块通信）](http://www.cnblogs.com/luoxn28/p/5440882.html)

