
# 控制盒(Controlling box)

## 块级元素与块盒(Block-level elements and block boxes)

**块级元素(Block-level elements)** 是'display'属性为：'block'，'list-item'和'table'的元素。块级元素生成**块级盒(Block-level boxes)**。块级盒参与块格式化上下文。

**块容器元素(block container element)** 是'display'属性为：'block', 'list-item'和'inline-block'的元素。块容器元素生成**块容器盒(block container box)**。


block-level element 生成 block-level box。block-level box 参与 块格式化上下文。
block container element 生成 block container box。block container box 有可能参与 块格式化上下文 也有可能参与 行内格式化上下文。


## 行内元素与行内盒(Inline-level elements and inline boxes)

**行内级元素(Inline-level elements)** 是'display'属性为： 'inline', 'inline-table', and 'inline-block' 的元素。行内级元素生成**行内级盒(inline-level boxes)**。行内级盒参与行内格式化上下文。

inline-level boxes 分为两类：inline boxes 与 atomic inline-level boxes。 inline box使用它的内容参与行内格式化上下文；atomic inline-level box 作为一个盒子(block container box)参与行内格式化上下文。

# 常规流(Normal flow)

常规流中，块盒与行内盒属于一个格式化上下文。
* 块级盒参与块格式化上下文
* 行内级盒参与行内格式化上下文。

## 块格式化上下文(Block formatting contexts)

* 在一个块格式化上下文中，从包含块的顶部开始，块级盒在竖直方向一个接一个地放置
* 两个兄弟盒之间的竖直距离由'margin'属性决定
* 同一个块格式化上下文中的相邻块级盒之间的竖直margin会合并
* 在一个块格式化上下文中，每个盒的left外边挨着包含块的left边（对于从右向左的格式化，right边挨着）。即使存在浮动，这也成立
* 浮动，绝对定位元素，非块盒的块容器（例如，inline-blocks，table-cells和table-captions）和'overflow'不为'visible'的块盒（当该值已被传播到视口时除外（except when that value has been propagated to the viewport））会为它们的内容建立一个新的块格式化上下文
