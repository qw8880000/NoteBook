---
title: 修改文章内链接样式 ｜ hexo
date: 2017-10-20 11:17:29
categories:
    - hexo
tags:
    - hexo
    - hexo next
abbrlink: cfa679e58e227dbc
---

针对 hexo next 主题，不过其他主题也大同小异。

## 效果

![image](http://oxnimkw03.bkt.clouddn.com/20171020113108.png)

以下是方法

## 新增配置

在主题配置文件`theme/next/_config.yml`，新增配置项：
```
custom_css:
  # the style of post body link
  post_body_a:
    enable: true
    normal_color: "#0593d3"
    hover_color: "#0477ab"
```

## 修改样式文件

next主题提供了用户自定义样式的扩展功能，我们只需要在`theme/next/source/css/_custom/custom.styl`里添加样式就可以新增或覆盖原来的样式。
```
// custom.styl
if hexo-config("custom_css.post_body_a.enable")
  .post-body
    a{
      color: convert(hexo-config("custom_css.post_body_a.normal_color"));
      border-bottom: none;
      &:hover {
        color: convert(hexo-config("custom_css.post_body_a.hover_color"));
        text-decoration: underline;
      }
    }
```
这里，我们用了`hexo-config()`函数读取配置，用stylus的内建函数`convert()`转换成stylus需要的颜色格式。

这个方法最大的优点就是可配置，也支持随时还原成原来主题的格式。

## 更多

更多内容参考：[hexo博客搭建汇总](http://www.wangjinle.com/posts/cc468aea3c750228.html)
