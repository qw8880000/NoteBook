---
title: protractor 安装时出现的问题
date: 2018-02-26 17:13:04
categories:
  - 前端
  - angular.js
tags:
  - angular.js
abbrlink: @@abbrlink
---

在安装protractor过程中，执行`webdriver-manager update`时出现如下错误：
```
$ webdriver-manager update
[17:03:14] I/update - geckodriver: file exists C:\Users\Administrator\AppData\Roaming\nvm\v6.8.0\node_modules\protractor\node_modules\webdriver-manager\selenium\geckodriver-v0.19.1.zip
[17:03:14] I/update - geckodriver: unzipping geckodriver-v0.19.1.zip
[17:03:14] I/update - geckodriver: geckodriver-v0.19.1.exe up to date
[17:03:33] E/downloader - Connection timeout downloading: https://chromedriver.storage.googleapis.com/2.35/chromedriver_win32.zip. Default timeout is 4 minutes.
[17:03:33] I/update - chromedriver: file exists C:\Users\Administrator\AppData\Roaming\nvm\v6.8.0\node_modules\protractor\node_modules\webdriver-manager\selenium\chromedriver_2.35.zip
[17:03:33] I/update - chromedriver: unzipping chromedriver_2.35.zip
[17:03:33] I/update - chromedriver: chromedriver_2.35.exe up to date
events.js:160
      throw er; // Unhandled 'error' event
      ^

Error: connect ETIMEDOUT 172.217.160.112:443
    at Object.exports._errnoException (util.js:1026:11)
    at exports._exceptionWithHostPort (util.js:1049:20)
    at TCPConnectWrap.afterConnect [as oncomplete] (net.js:1085:14)

```

原因是`Error: connect ETIMEDOUT 172.217.160.112:443`，说明在下载某一个软件包的时候遇到了网络问题。然后找了一下错误信息发现`[17:03:33] E/downloader - Connection timeout downloading: https://chromedriver.storage.googleapis.com/2.35/chromedriver_win32.zip. Default timeout is 4 minutes.`，这里提示了我们下载`chromedriver_win32.zip`超时了。我的解决方案是把下载失败的软件包的链接改用迅雷或其他工具进行下载，然后把下载完成的软件包放到对应的目录里。

也就是说使用`webdriver-manager update`查看哪些包下载不了，然后改用其他方式下载，再放在对应的目录中去。 

