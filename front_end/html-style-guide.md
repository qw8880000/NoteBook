---
title: html 编码规范
date: 2018-06-15 13:00:09
categories:
  - 前端
  - html
tags:
  - html
abbrlink: 3a7f06b80c157516
---

不管有多少人共同参与同一项目，一定要确保每一行代码都像是同一个人编写的。

# 格式

* 用两个空格来代替制表符（tab） -- 这是唯一能保证在所有环境下获得一致展现的方法。
* 嵌套元素应当缩进一次（即两个空格）。

# 语法

* 自闭合（self-closing）标签，无需闭合 ( 例如： `img` `input` `br` `hr` 等 )；
* 可选的闭合标签（closing tag），需闭合 ( 例如：`</li>` 或 `</body>` )；

```html
<img src="images/google.png" alt="Google">
<input type="text" name="title">

<ul>
  <li>Style</li>
  <li>Guide</li>
</ul>
```

* 对于属性的定义，确保全部使用双引号，绝不要使用单引号。

```html
<!-- Not recommended -->
<span id='j-hook' class=text>Google</span>

<!-- Recommended -->
<span id="j-hook" class="text">Google</span>
```

# 嵌套

`a` 不允许嵌套 `div` 这种约束属于语义嵌套约束，与之区别的约束还有严格嵌套约束，比如`a` 不允许嵌套 `a`。

严格嵌套约束在所有的浏览器下都不被允许；而语义嵌套约束，浏览器大多会容错处理，生成的文档树可能相互不太一样。

**语义嵌套约束**

* `<li>` 用于 `<ul>` 或 `<ol>` 下；
* `<dd>`, `<dt>` 用于 `<dl>` 下；
* `<thead>`, `<tbody>`, `<tfoot>`, `<tr>`, `<td>` 用于 `<table>` 下；

**严格嵌套约束**

* inline-Level 元素，仅可以包含文本或其它 inline-Level 元素;
* `<a>`里不可以嵌套交互式元素`<a>`、`<button>`、`<select>`等;
* `<p>`里不可以嵌套块级元素`<div>`、`<h1>~<h6>`、`<p>`、`<ul>/<ol>/<li>`、`<dl>/<dt>/<dd>`、`<form>`等。

更多详情，参考[WEB标准系列-HTML元素嵌套](http://www.smallni.com/element-nesting/)

# HTML5 doctype

为每个 HTML 页面的第一行添加标准模式（standard mode）的声明，这样能够确保在每个浏览器中拥有一致的展现。

```html
<!DOCTYPE html>
<html>
  <head>
  </head>
</html>
```

# IE 兼容模式

IE 支持通过特定的 `<meta>` 标签来确定绘制当前页面所应该采用的 IE 版本。除非有强烈的特殊需求，否则最好是设置为 edge mode，从而通知 IE 采用其所支持的最新的模式。

[阅读这篇 stack overflow 上的文章](http://stackoverflow.com/questions/6771258/whats-the-difference-if-meta-http-equiv-x-ua-compatible-content-ie-edge-e)可以获得更多有用的信息。

```html
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```

# 字符编码

通过明确声明字符编码，能够确保浏览器快速并容易的判断页面内容的渲染方式。这样做的好处是，可以避免在 HTML 中使用字符实体标记（character entity），从而全部与文档编码一致（一般采用 `UTF-8` 编码）。

```html
<head>
  <meta charset="UTF-8">
</head>
```

# 属性顺序

HTML 属性应当按照以下给出的顺序依次排列，确保代码的易读性。

1. `class`
1. `id`, `name`
1. `data-*`
1. `src`, `for`, `type`, `href`, `value`
1. `title`, `alt`
1. `role`, `aria-*`

class 用于标识高度可复用组件，因此应该排在首位。id 用于标识具体组件，应当谨慎使用（例如，页面内的书签），因此排在第二位。

```html
<a class="..." id="..." data-toggle="modal" href="#">
  Example link
</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

# 减少标签的数量

编写 HTML 代码时，尽量避免多余的父元素。很多时候，这需要迭代和重构来实现。请看下面的案例：

```html
<!-- Not so great -->
<span class="avatar">
  <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
```

# 参考

* [html&css编码规范](http://codeguide.bootcss.com/)
* [html&css style guide](https://github.com/Aaaaaashu/Guide)
