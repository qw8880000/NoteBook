

## 蓝牙模块

* 按照协议标准划分：2.0 2.1 3.0 4.0 4.1 等
* 按照芯片设计划分：
    * rom方案： 
        ROM版模块采用芯片厂家的ROM版芯片，
        特点是芯片厂家将标准的应用PROFILES固化在芯片中，
        用户无法对芯片内程序进行修改，适合大规模的批量生产，
        价格很低，如蓝牙耳机模块、手机模块、鼠标键盘模块等。
    * flash方案：
        芯片内置了FLASH存储，用户可以定制自己的应用，烧写到模块中的flash
    * 基于Host端系统的蓝牙：
        蓝牙协议栈必须运行在Host 平台系统上，而不是蓝牙模块内。
        蓝牙功能的应用取决于系统上蓝牙协议栈的支持（基本上可以涵盖所有的蓝牙功能）
* 其他分类

## 蓝牙模块的单模与双模

* 单模：只支持 BLE
* 双模：支持classic bluetooth 和 BLE

![iamge](../images/single_mode_and_double_mode.jpg)

## 参考
* [蓝牙模块的种类](http://www.yinglab.com/Bluetooth/6.html)
* [蓝牙4.0技术介绍](https://wenku.baidu.com/view/b9ab1471866fb84ae55c8d40.html)

