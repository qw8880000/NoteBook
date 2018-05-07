---
title: sass(css) 分层构架
date: 2018-05-07 17:14:41
categories:
  - 前端
  - css
tags:
  - css
  - sass
abbrlink: @@abbrlink
---

```
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
