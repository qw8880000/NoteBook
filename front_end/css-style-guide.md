---
title: javascript 学习汇总
date: 2018-06-14 15:52:09
categories:
  - 前端
  - css
tags:
  - css
abbrlink: @@abbrlink
---

不管有多少人共同参与同一项目，一定要确保每一行代码都像是同一个人编写的。

# 格式

* 缩进使用`2`个空格。
* 为选择器分组时，每个选择器独占一行。
* 为了代码的易读性，在每个声明块的左花括号前添加一个空格。
* 声明块的右花括号应当单独成行。
* 每条声明语句的` : `后应该插入一个空格。
* 为了获得更准确的错误报告，每条声明都应该独占一行。
* 所有声明语句都应当以分号结尾。
* 对于以逗号分隔的属性值，每个逗号后面都应该插入一个空格（例如，`box-shadow`）。
* 不要在 `rgb()`、`rgba()`、`hsl()`、`hsla()` 或 `rect()` 值的内部的逗号后面插入空格。这样利于从多个属性值（既加逗号也加空格）中区分多个颜色值（只加逗号，不加空格）。


```css
/* Bad CSS */
.selector, .selector-secondary, .selector[type=text] {
  padding:15px;
  margin:0px 0px 15px;
  background-color:rgba(0, 0, 0, 0.5);
  box-shadow:0px 1px 2px #CCC,inset 0 1px 0 #FFFFFF
}

/* Good CSS */
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin-bottom: 15px;
  background-color: rgba(0,0,0,.5);
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
```

**例外及细微偏移原则的情况**

对于大量仅包含单条声明的声明块，可以使用一种略微不同的单行格式。在这种情况下，在左大括号之后及右大括号之前都应该保留一个空格。

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

对于以逗号分隔并且非常长的属性值 -- 例如一堆渐变或者阴影的声明 -- 可以放在多行中，这有助于提高可读性，并易于生成有效的diff。这种情况下有多 种格式可以选择，以下展示了一种格式。

```css
.selector {
    box-shadow:
        1px 1px 1px #000,
        2px 2px 1px 1px #ccc inset;
    background-image:
        linear-gradient(#fff, #ccc),
        linear-gradient(#f3c, #4ec);
}
```

# 语法

* 对于属性值或颜色参数，省略小于 `1` 的小数前面的 `0` （例如，`.5` 代替 `0.5`；`-.5px` 代替 `-0.5px`）。
* 十六进制值应该全部小写，例如，`#fff`。在扫描文档时，小写字符易于分辨，因为他们的形式更易于区分。
* 为选择器中的属性添加双引号，例如，`input[type="text"]`。只有在某些情况下是可选的，但是，为了代码的一致性，建议都加上双引号。
* 避免为 `0` 值指定单位，例如，用 `margin: 0`; 代替 `margin: 0px`;。

# 声明顺序

相关的属性声明应当归为一组，并按照下面的顺序排列：

1. Positioning
1. Box model
1. Typographic
1. Visual

由于定位（positioning）可以从正常的文档流中移除元素，并且还能覆盖盒模型（box model）相关的样式，因此排在首位。盒模型排在第二位，因为它决定了组件的尺寸和位置。

其他属性只是影响组件的内部（inside）或者是不影响前两组属性，因此排在后面。

```css
.declaration-order {
  /* Positioning */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;

  /* Box-model */
  display: block;
  float: right;
  width: 100px;
  height: 100px;

  /* Typography */
  font: normal 13px "Helvetica Neue", sans-serif;
  line-height: 1.5;
  color: #333;
  text-align: center;

  /* Visual */
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  /* Misc */
  opacity: 1;
}
```

# 注释

注释的风格应当简洁，并在代码库中保持统一。

```
/* ==========================================================================
   区块代码注释
   ========================================================================== */

/* 次级区块代码注释
   ========================================================================== */

/**
 * “Doxygen式注释格式”的简短介绍
 *
 * 这里可以书写较长的说明文本。
 *
 * @tag 这是一个叫做“tag”的标签。
 *
 * TODO: 这个“‘需做’陈述”描述了一个接下来要去做的小工作。这种文本，
 *   如果超长了的话，应该在80个半角字符（如英文）或40个全角字符（
 *   如中文）后便换行，并（在“ * ”的基础上）再在后面缩进两个空格。
 */

/* 一般的注释 */
```

# Class 命名

* 使用有意义的名称。
* class 名称中只能出现小写字符和破折号（dashe）。
* 遵循所使用的css框架的命名规范，或者类BEM的命名：

```css
/* [BEM](https://en.bem.info/methodology/quick-start/) */
/*
 * block
 * block__element
 * block__element--modifier
 */
.list {...}
.list__item {...}
.list__item--active {...}
```

# 媒体查询（Media query）的位置

将媒体查询放在尽可能相关规则的附近。不要将他们打包放在一个单一样式文件中或者放在文档底部。如果你把他们分开了，将来只会被大家遗忘。下面给出一个典型的实例。

```css
.element { ... }
.element-avatar { ... }
.element-selected { ... }

@media (min-width: 480px) {
  .element { ...}
  .element-avatar { ... }
  .element-selected { ... }
}
```

# 简写形式的属性声明

在需要设置所有值的情况下，应当尽量限制使用简写形式的属性声明; 反之，一般情况下不使用简写。

```css
/* Bad example */
.element {
  margin: 0 0 10px;
  background: red;
  background: url("image.jpg");
  border-radius: 3px 3px 0 0;
}

/* Good example */
.element {
  margin-bottom: 10px;
  background-color: red;
  background-image: url("image.jpg");
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
}
```

# 预处理：Sass 与 Less

* 将嵌套深度限制在`1`级。对于超过`2`级的嵌套，给予重新评估。这可以避免出现过于详实的CSS选择器。
* 避免大量的嵌套规则。当可读性受到影响时，将之打断。推荐避免出现多于20行的嵌套规则出现。
* 始终将`@extend`语句放在声明块的第一行。如果可以的话，将`@include`语句放在声明块的顶部，紧接着`@extend`语句的位置。
* 考虑在自定义函数的名字前加上`x-`或其它形式的前缀。这有助于避免将自己的函数和CSS的原生函数混淆，或函数命名与库函数冲突。

```css
.selector-1 {
    @extend .other-rule;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // other declarations
}
```

扩展阅读：[Nesting in Sass and Less](http://markdotto.com/2015/07/20/css-nesting/)

# 参考

* [html&css编码规范](http://codeguide.bootcss.com/)
* [Principles of writing consistent, idiomatic CSS](https://github.com/necolas/idiomatic-css)
