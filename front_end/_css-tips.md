# line-height 无法作用于替换元素

`line-height` 无法作用于替换元素(img等)。如果对一个`img`元素设置`display:inline-block; line-height: xx;`是无法使`img`元素获得行间距的。

# vertical-align 与 baseline

* [[翻译]关于Vertical-Align你需要知道的事情](https://segmentfault.com/a/1190000002668492)
* [Vertical-Align: All You Need To Know](http://christopheraue.net/2014/03/05/vertical-align/)


如何确定一个元素的baseline:
```
inline类为小写字母x的底端。inline-block类其内没有inline类型时，baseline为盒子模型的底端；inline-block类其内有inline类型时，baseline为其内最后一行inline的baseline（即最后一行小写x的底端）
```

如何确定父元素的baseline:
```
line-box的baseline是不可见的，但是可以很轻松的将它可视化出来，在行的开头添加一个字母，比如'x'，这个字母的下边界默认就是baseline的位置
```

vertical-align: middle对齐的方式是：
```
vertical-align对齐的点是baseline加上半个x的距离(half of the x-height)
```

# box-sizing

https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-sizing

# 伪类的顺序

伪类先后顺序被称为LVHA顺序: `:link — :visited — :hover — :active`。CSS层叠中有一条法则十分重要，就是后面覆盖前面，所以伪类的顺序是需要精心考虑的。
当点击按下未放开时，此时触发active，但是此时hover也要触发，为了看到active的效果，那么active就必须放在hover后面；

# 元素<a>的visited颜色问题

a在点击后会变成另一个颜色，有没有办法让a在visited状态的颜色与正常状态下的颜色保持不变？答案是并没有这样的设置项，不过可以这样声明：
```
a, a:visited {
  color: inherit;
}
```
