

## android studio 熟悉

* [ANDROID STUDIO详细教程汇总](http://stormzhang.com/devtools/2015/06/17/android-studio-all/)

## 快捷键

* 删除没用的import  `ctrl + alt + o`

## 关于Gradle

有两个概念要理清楚：
* Google Gradle plugin
    gradle plugin 是谷歌为android studio推出的一个gradle插件。
* Gradle  
    gradle是一个构建工具。

需要学会如何查看gradle版本与gradle plugin版本

**查看本地的gradle版本**
1. Win平台会默认下载到 `C:\Documents and Settings<用户名>.gradle\wrapper\dists` 目录，可以到这个目录查看

**查看本地的gradle plugin版本**
1. `File->settings->plugins->Gradle`

**查看项目需要的gradle版本**
1. `your_project/gradle/wrapper/gradle-wrapper.properties` 
```
distributionBase=GRADLE_USER_HOME
distributionPath=wrapper/dists
zipStoreBase=GRADLE_USER_HOME
zipStorePath=wrapper/dists
distributionUrl=https\://services.gradle.org/distributions/gradle-2.1-all.zip
```
说明版本是 2.1

**查看项目需要的gradle plugin版本**
1. `your_project/build.gradle` 中的`dependencies`
```
    dependencies {
        classpath 'com.android.tools.build:gradle:0.14.1'
    }
```
说明使用的是 0.14.1版本

1. 打开终端，切换到你的项目目录，运行`./gradlew -v`


参考：
* [给 ANDROID 初学者的 GRADLE 知识普及](http://stormzhang.com/android/2016/07/02/gradle-for-android-beginners/)
* [Android Studio中Gradle使用详解](http://www.jianshu.com/p/02cb9a0eb2a0)
* [Gradle版本管理-升级与降级](http://hucaihua.cn/2016/09/27/Gradle_upgrade/)

