
```batch
route delete 0.0.0.0

:: (外网)设置所有网络走 192.168.40.1 网关， metric 10 是设置优先级别
route add 0.0.0.0 mask 0.0.0.0 192.168.40.1 metric 10 if 4

:: (内网)设置访问192.168网段的网络走192.168.1.1网关
route add 192.168.0.0 mask 255.255.0.0 192.168.1.1 metric 20 if 30
```

注意：路由配置一定要设置对应的接口。运行`route print` 查看：
```
===========================================================================
接口列表
 30...7c dd 90 48 3c 46 ......Microsoft Wi-Fi Direct Virtual Adapter
 35...7c dd 90 48 3c 47 ......Microsoft Wi-Fi Direct Virtual Adapter #2
  4...a4 1f 72 5e fb 62 ......Realtek PCIe GBE Family Controller
 24...7c dd 90 48 3c 44 ......802.11n USB Wireless LAN Card
  1...........................Software Loopback Interface 1
  6...00 00 00 00 00 00 00 e0 Microsoft Teredo Tunneling Adapter
===========================================================================
```