---
title: angualr.js 架构
date: 2018-05-09 17:37:46
categories:
  - 前端
  - angular.js
tags:
  - angular.js
abbrlink: @@abbrlink
---

# 概览

此angular.js架构是我在开发一个web端的后台管理系统时，学习了[johnpapa/angular-styleguide]的架构后，在实践中经过些许小调整后总结出的心得。此项目是一个单面应用，整体架构如下所示：

```
    app.module.js
        |
        |-- /blocks                     # 跨app的模块
        |   |
        |   |-- /exception
        |   |-- /logger
        |   \-- ..
        |
        |
        |-- /core                       # app通用模块
        |-- /utils                      # app通用模块
        |-- /widgets                    # app通用模块
        |
        |
        \-- /features                   # 功能模块
            |
            |-- app.feature1
            |-- app.feature2
            |-- app.feature3
            \-- ...

```

angualr.js架构总体上分为三个部分：app功能模块，app通用模块，跨app通用模块。

* `app.module.js`: 根模块。
* `/blocks`：跨app的通用模块。如 blocks.exception, blocks.logger。
* `/core` `/widgets` `/utils`：此app的通用的模块。
* `/features`：app的功能模块。

# app.module.js

`app.module.js` 是angular.js目录下的根文件，它是整个项目中的根模块，包含着整个项目使用到的其他模块。这个文件的内容通常是声明一个模块并添加它的依赖，例如：
```js
angular
    .module('app', [

      /*
       *  3rd party angular modules
       */
      'ngResource',
      'ngAnimate',
      'ngCookies',
      'ngSanitize',
      'ngLocale',
      'ui.router',

      /*
       * Our reusable cross app code modules
       */
      'ccWidget',
      'blocks.logger',

      /*
       *  app common area
       */
      'app.core',
      'app.utils',
      'app.widgets',

      /*
       * feature area
       */
      'app.login',
      'app.home',
      'app.dashboard',
      'app.shops',
    ]);
```

如果是单页应用，通常根目录下只放`app.module.js`文件，如上面所示；如果是多页应用，根目录下可以放置多个文件，对应多个页面。

# Blocks

`/blocks` 目录的作用是存放跨aqq的模块。也就是说blocks下面的模块非常接近第三方库，可以轻易的在多个项目中使用。比如，我的`/blocks`目录下有一个`cc-widget`模块，其中有`accordion`、`file-input`、`modal`等模块，这些模块通用性很强，甚至可以直接封装成第三方库。

# Core | Utils | Widgets

`/core`、`/utils`、`/widgets`这三个模块是项目中的通用模块。

* `/core` 主要是存放配置和一些服务，比如：
  - route.config.js: 页面切换的路由配置
  - route.service.js: 页面切换时的权限鉴定服务
  - http.config.js: http模块配置，如http request header配置
  - http-exception.service.js: http异常处理服务
  - authentication.service.js: 权限相关接口
  - core.constant.js: 存放数据常量
  - core.run.js: app启动代码，进行一些必要的项目初始化
*  `/utils` 存放工具型接口的模块，比如：
  - qiniu.service.js: 七牛sdk代码
  - md5.service.js: md5接口
* `/widgets` 存放组件，比如：
  - img-cropper.component.js: 图片裁剪组件
  - datepicker-group.component.js: 时间范围选择组件
  - nav-menu.component.js: 菜单栏组件
  - dialog.service.js: 对话框接口

# Features

`/features` 目录存放具体的功能或者业务，比如：
* /home
* /login
* /dashboard
* /wallet   # 钱包
* /orders   # 订单

# 总结

架构的主要目的是分层，每一层下再分模块，这样代码结构清晰，当上层业务出现可重用代码时，可以抽象出来往下层存放，就可以保持高质量，高可维护性的代码。

# 例子

这里有一个例子，使用了上述的angular.js架构：[qw8880000/angularjs-sample](https://github.com/qw8880000/angularjs-sample)









[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

[angular.js code style]: <https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md>
