
# java 为什么是跨平台

因为Java程序编译之后的代码不是能被硬件系统直接运行的代码，而是一种“中间码”——字节码。然后不同的硬件平台上安装有不同的Java虚拟机(JVM)，由JVM来把字节码再“翻译”成所对应的硬件平台能够执行的代码。

但是，不同的硬件上需要对应的JVM虚拟机。也就是java是跨平台，而JVM是与硬件相关。

# java 基础语法

1. 大小写敏感：Java是大小写敏感的，这就意味着标识符Hello与hello是不同的。
1. 类名：对于所有的类来说，类名的首字母应该大写。如果类名由若干单词组成，那么每个单词的首字母应该大写，例如 MyFirstJavaClass 。
1. 方法名：所有的方法名都应该以小写字母开头。如果方法名含有若干单词，则后面的每个单词首字母大写。
1. 源文件名：源文件名必须和类名相同。当保存文件的时候，你应该使用类名作为文件名保存（切记Java是大小写敏感的），文件名的后缀为.java。 （如果文件名和类名不相同则会导致编译错误）。
1. 主方法入口：所有的Java 程序由`public static void main(String []args)`方法开始执行。

# 学习材料

- [java下载 - orace](https://www.oracle.com/cn/java/technologies/downloads/)
- [廖雪峰的java教程](https://www.liaoxuefeng.com/wiki/1252599548343744)
- [java教程 - C语言中文网](http://c.biancheng.net/java/)

# 学习心得
看了<head firt java>的‘继承与多态’ 和 ‘接口与抽象类’ 2章，比较好的一点是讲解了继承的作用，多态的作用，接口的作用，这样就明白了为什么需要他们。
<java基础教程> 就比较偏语法书，而且没有讲泛型。

# maven

- [Apache Maven](https://maven.apache.org/)
- [Maven 教程](https://www.w3cschool.cn/maven/)
- maven 配置国内maven仓库：[阿里云Maven中央仓库](https://developer.aliyun.com/mvn/guide)


# 简介

先学习`spring`，再学习`spring boot`

# spring

`spring` 学习材料：
* [spring教程 - w3cschool](https://www.w3cschool.cn/wkspring/index.html) 
* [spring-sample](https://github.com/qw8880000/spring-samples)

- [图文教程教你IDEA中的Spring环境搭建+简单入门](https://www.huhexian.com/143291.html)
- [Spring 教程 - BootWiki](https://www.bootwiki.com/spring/spring-bean-definition.html)
# spring boot

- [Spring Boot 5分钟快速教程](https://zhuanlan.zhihu.com/p/555734770)
- [Spring Boot教程 - BootWiki](https://www.bootwiki.com/springboot/spring-boot-tutorial.html)
- [spring-boot-demo - github](https://github.com/xkcoding/spring-boot-demo/tree/master/demo-admin/admin-client)

- [Spring Boot Reference Guide](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#boot-documentation)

# spring boot jpa

https://spring.io/guides/gs/accessing-data-jpa/


## 编译时如果有外部依赖如何处理

使用 -classpath参数指定依赖的位置。

这里需要关注一下package。package相当于一个命名空间，当一个类放在一个package中的时候，这个类的全名是`package.class`，以下代码`Boss`类的全名应该是`com.payroll.Boss`。

```java
package com.payroll;

public class Boss
{
   public void payEmployee(Employee e)
   {
      e.mailCheck();
   }
}

```

一个类的完整名字是"package.class"。当javac程序在编译的时候，在解析 import 语句的时候，会把package.class 中的package作为相对路径，结合 classpath 路径去找到对应的类。
比如，指定classpath为 c:/java，然后另一个java文件的import语句为 `com.payroll.Boss;`, 那么java编译器会到 `c:/java/com/payroll`目录下去查找Boss.java类。

编译与运行的时候都是相同的原理。

## 运行时如果有外部依赖如何处理

使用 -classpath参数指定依赖的位置

## html 转 pdf

WKHTMLTOPDF  https://wkhtmltopdf.org/

## selenium

selenium官网：http://www.seleniumhq.org/

- selenium-Google驱动下载 http://chromedriver.storage.googleapis.com/index.html
- selenium-firefox驱动下载：https://registry.npmmirror.com/binary.html?path=geckodriver/


## java 爬虫
webmagic 很好上手
- [webmagic.io](http://webmagic.io/docs/zh/)

## SLF4J 日志系统

- [SLF4J 日志系统](http://www.51gjie.com/javaweb/1123.html)
- log4j 配置说明 https://www.cnblogs.com/TheGCC/p/14552073.html
- [log4j 详细讲解（不能再详细了）](https://blog.csdn.net/u012422446/article/details/51199724)

## 如何简单下载网页上的m3u8视频 - vlc 流媒体播放器

使用vlc media player，命令行模式播放m3u8流视频
```shell
./vlc.exe "https://xxx/mp4/xxx.mp4/index.m3u8"
```

vlc说明：执行 `vlc -H` 会在当前路径中生成vlc-help.txt，这里有很详细的vlc命令行参数说明

### vlc --sout参数使用方法

vlc --sout 参数流输入语法参考：
```
vlc input_stream --sout "#module1{option1=parameter1{parameter-option1},option2=parameter2}:module2{option1=...,option2=...}:..."
```
或者使用以下语法：
```
vlc input_stream --sout-module1-option1=... --sout-module1-option2=... --sout-module2-option1=... --sout-module2-option2=... ...
```


参考：
- vlc的流输出功能:https://blog.csdn.net/weixin_30861797/article/details/95410326
- vlc命令行使用方法:https://wiki.videolan.org/Documentation:Streaming_HowTo/Advanced_Streaming_Using_the_Command_Line/
- vlc使用说明: https://wiki.videolan.org/Documentation:Streaming_HowTo/

### vlc 把视频流保存成文件

把网络视频流保存成文件：
```
vlc "https://hhhh.mp4" --sout="#standard{access=file,mux=ts,dst='test.mp4'}"
```

### 命令行启动vlc后，vlc无法自动退出问题解决
在java代码中，通过 runtime.exec执行vlc命令下载视频流，发现最后视频下载完成后vlc界面没有自动退出，导致process.waitFor() 一直在等待，尝试了vlc各种参数命令后都无法解决这个问题，后面是通过在命令行中加入`vlc://quit`解决：
```java
    Runtime runtime = Runtime.getRuntime(); //获取Runtime实例
    String command = String.format("vlc \"%s\" --sout=\"#standard{access=file,mux=ts,dst='%s'}\" vlc://quit", video_src, video_output);
    Process process = runtime.exec(command);

    // 标准错误流（必须写在 waitFor 之前）
    InputStream errInputStream = process.getErrorStream();
    int proc = process.waitFor();

    if (proc == 0) {
        LOGGER.info("执行成功");
    } else {
        LOGGER.warn("vlc执行失败");
    }
```



## jdbc 数据库连接

- [jdbc教程 - 易百](https://www.yiibai.com/jdbc/)
- [HikariCP - github](https://github.com/brettwooldridge/HikariCP)
- [3w字教程：JDBC从零到熟练掌握Druid的使用](https://zhuanlan.zhihu.com/p/486099129)


## Jsoup

- [Jsoup 官方网站](https://jsoup.org/)


## POJO

POJO（Plain Ordinary Java Object）简单的Java对象，实际就是普通JavaBeans，是为了避免和EJB混淆所创造的简称。它不具备业务逻辑处理方法（当然，如果你有一个简单的运算属性也是可以的，但不允许有业务方法），它是只有一些属性及其getter setter方法的类。

- [java EJB pojo是什么](http://www.360doc.com/content/22/1027/12/20880499_1053481665.shtml)

## mybatis

- [MyBatis-Plus - 苞米豆](https://baomidou.com/)
- [MyBatis教程 - 易百教程](https://www.yiibai.com/mybatis/install_configure.html)
- [MyBatis教程 - C语言中文网](http://c.biancheng.net/mybatis/)
- [MyBatis教程](https://mybatis.org/mybatis-3/zh/index.html)
- [MyBatis教程 - W3Cschool](https://www.w3cschool.cn/mybatis/)

## IDE - intelliJ IDEA

插件：
- maven-search 用来搜索java依赖

## ffmpeg 把mp4转成M3U8

./ffmpeg.exe -i D:\\王锦乐\\nginx-1.24.0\\html\\test\\38c7c56e33d931e5c4cf\\38c7c56e33d931e5c4cf.MP4 -c:v copy -hls_time 2  -hls_segment_filename D:\\王锦乐\\nginx-1.24.0\\html\\test\\38c7c56e33d931e5c4cf\\%d.ts -f hls D:\\王锦乐\\nginx-1.24.0\\html\\test\\38c7c56e33d931e5c4cf\\38c7c56e33d931e5c4cf.m3u8

首先来把MP4切片成ts，然后创建m3u8，我目前了解到的m3u8其实就是一个类似于清单，播放器读取后，根据这个清单来按序播放ts视频

ffmpeg -i demo.mp4 -profile:v baseline -level 3.0 -start_number 0 -hls_time 10 -hls_list_size 0 -f hls demo.m3u8

其中demo.mp4和demo.m3u8就是原文件和需要转换成的m3u8文件；

-profile:v baseline 大概意思是档次转成基本画质，有四种画质级别,分别是baseline, extended, main, high，从低到高

-level 3.0 大概也是视频画质级别吧，基本上是从1到5,

-start_number 0 表示从0开始

-hls_time 10 标识每10秒切一个



-i 1523786410.mp4 -profile:v baseline -level 3.0 -start_number 0 -hls_time 10 -hls_list_size 0 -f hls demo.m3u8