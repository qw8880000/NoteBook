快要被surface屏幕亮度自动调节折磨死了，网上的很多方法都不管用，不管是显示设置里关闭亮度自动调节，还是服务里关闭相应的服务都不起作用。
后来在surface5贴吧里看到一个方法，是关闭显示器节能技术，终于成功解决。

这里记录一下，我的电脑是surface 5，显卡是inter graphics 620。

# 方法一

解决方法：

* 到inter官网下载官方驱动
* 安装驱动后有一个显卡控制面板，把显示器节能技术禁用即可

![image](http://qiniu.wangjinle.com/surface_%E5%85%B3%E9%97%AD%E5%B1%8F%E5%B9%95%E4%BA%AE%E5%BA%A6%E8%87%AA%E5%8A%A8%E8%B0%83%E8%8A%82.png)

或者

![image-20210113132608381](http://qiniu.wangjinle.com/image-20210113132608381.png)

# 方法二

打开注册表编辑器，打开如下路径：
计算\HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Class{4d36e968-e325-11ce-bfc1-08002be10318}\0001
打开图中FeatureTestControl注册表，修改数值9240为9250，如果是200改为210
