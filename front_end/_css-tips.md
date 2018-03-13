# line-height 无法作用于替换元素

`line-height` 无法作用于替换元素(img等)。如果对一个`img`元素设置`display:inline-block; line-height: xx;`是无法使`img`元素获得行间距的。

# vertical-align

`vertical-align`并不是真正的垂直居中

# box-sizing

https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-sizing

# 伪类的顺序

伪类先后顺序被称为LVHA顺序: `:link — :visited — :hover — :active`。CSS层叠中有一条法则十分重要，就是后面覆盖前面，所以伪类的顺序是需要精心考虑的。
当点击按下未放开时，此时触发active，但是此时hover也要触发，为了看到active的效果，那么active就必须放在hover后面；
