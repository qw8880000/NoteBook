---
title: sass(css) 分层构架
date: 2018-05-07 17:14:41
categories:
  - 前端
  - css
tags:
  - css
  - sass
abbrlink: 41e9a627e79a87c2
---

# 概览

我所使用的sass架构参考自这篇文章[Architecture for a Sass Project](https://www.sitepoint.com/architecture-sass-project/)，并根据我自身对sass的理解做了一些调整。

sass整体目录分层结构如下所示：

```
/sass
|
|-- app.scss
|
|-- /vendors
|
|-- /helpers
|   |
|   |-- _functions.scss
|   |
|   |-- /mixins
|   |   |-- _border_radius.scss
|   |   |-- _box-shadow.scss
|   |   |-- _button.scss
|   |   |-- ...
|   |
|   \-- /variables
|       |-- _base.scss
|       |-- _components.scss
|       \-- _partials.scss
|       \-- _pages.scss
|
|
|-- /base
|   |-- _reset.scss
|   |-- _base.scss
|   \-- _utilities.scss
|
|
|-- /components
|   |-- _alert.scss
|   |-- _badge.scss
|   |-- _button.scss
|   |-- _form.scss
|   |-- ...
|
|
|-- /partials
|   |-- _header.scss
|   |-- _footer.scss
|   |-- _sidebar.scss
|   |-- ...
|
|-- /pages
|   |-- home.scss
|   |-- login.scss
|   |-- ...
|
|
\-- /themes
```

# app.scss

首先要注意的是根目录下的`app.scss`，这个文件用来引入各个模块(`/base`,`/components`,'/partials',`/pages`...)，并且用来生成最终的css文件。

`app.scss`文件的内容如下所示：
```scss
/* ==================================
 * Vendors
 * ================================== */
...

/* ==================================
 * Helpers
 * ================================== */
@import "helpers/_functions.scss";
@import "helpers/variables/_base.scss";
@import "helpers/variables/_components.scss";
@import "helpers/variables/_partials.scss";
@import "helpers/variables/_pages.scss";

@import "helpers/mixins/_badge.scss";
@import "helpers/mixins/_button.scss";
@import "helpers/mixins/_border_radius.scss";
@import "helpers/mixins/_box-shadow.scss";
...

/* ==================================
 * Base
 * ================================== */
@import "base/_reset.scss";
@import "base/_base.scss";
@import "base/_utilities.scss";

/* ==================================
 * Components
 * ================================== */
@import "components/_alert.scss";
@import "components/_badge.scss";
@import "components/_breadcrumb.scss";
@import "components/_button.scss";
...

/* ==================================
 * Partials
 * ================================== */
@import "partials/_header.scss";
@import "partials/_sidebar.scss";
@import "partials/_nav-menu.scss";
...

/* ==================================
 * Pages
 * ================================== */
@import "pages/_home.scss";
@import "pages/_login.scss";
...

/* ==================================
 * Themes
 * ================================== */
...
```

# Vendors

`/vendors` 用来放一些第三方库或者框架的css文件，比如Bootstrap、jQueryUI等。比如：

* bootstrap.scss
* jquery-ui.scss
* select2.scss


# Helpers

`/helpers` 目录用来存放sass的变量、函数、mixin。此目录下的所以文件均不会单独输出css样式，它们是为后面的模块而服务。比如：

* _functions.scss
* /mixins
  - _border_radius.scss
  - _box-shadow.scss
  - _button.scss
  - ...
* /variables
  - _base.scss
  - _components.scss
  - _partials.scss
  - _pages.scss
  - ...

# Base

`/base` 目录有以下三个文件：

* _reset.scss
* _base.scss
* _utilities.scss

`_reset.scss`存放浏览器重置样式；

`_base.scss`存放常用html元素的样式，如`h1, h2, h3, h4, h5, body, ul`等；

`_utilities.scss`用来存放一些重用度很高，粒度很小的工具型样式，如`.d-block { display: block; }`，`.text-center { text-align: center; }`等。

# Components

`/components` 目录看它的名字就知道是用来存放组件，比如：

* _alert.scss
* _badge.scss
* _button.scss
* _form.scss

# Partials

`/partials` 也是页面的模块，但是它比component要大，通常是一些component的组合，或者是一个较大的模块。比如：

* _header.scss
* _footer.scss
* _sidebar.scss
* _nav.scss

有一些模块看起来即可以放在`/partials`也可以放在`/components`，这个可以根据自己对模块粒度的把握，灵活调整。

# Pages

`/pages` 目录存放特定页面的特殊样式和整体页面的布局样式。比如：
* home.scss
* login.scss

# Themes

`/themes` 目录存放主题样式控制代码，适合有多个主题的网页。比如：
* _dark-theme.scss
* _light-theme.scss

# 例子

实例可参考：[angular.js sample scss](https://github.com/qw8880000/angularjs-sample/tree/master/src/client/scss)

# 参考

* [Sass: Directory Structures That Help You Maintain Your Code](http://vanseodesign.com/css/sass-directory-structures/)
* [Architecture for a Sass Project](https://www.sitepoint.com/architecture-sass-project/)
