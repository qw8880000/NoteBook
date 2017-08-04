@Filename:       vim_tabular插件.md
@Author:         wangjl
@Date:           2015-09-30 14:42
@Last modified:   2015-09-30 14:42
@Description:   

## tabular 简介

tabular 是一个文本对齐插件

## 使用

### example 1:

    Some short phrase,some other phrase
    A much longer phrase here,and another long phrase

>   :Tabularize /,

    Some short phrase         , some other phrase
    A much longer phrase here , and another long phrase

上述命令传入的匹配模式是',' 
tabular 默认左对齐
tabular 默认加入1个空格

>   :Tabularize /,/r0

            Some short phrase,      some other phrase
    A much longer phrase here,and another long phrase

指定对齐格式：l  r  c,分别表示左对齐，右对齐，居中对齐；
然后跟上数字表示添加的空格数。

>   :Tabularize /,/r1c1l0

            Some short phrase , some other phrase
    A much longer phrase here , and another long phrase

效果：逗号前面的右对齐，逗号后面的左对齐
上述命令解读：第一个逗号前的文本右对齐，然后1个空格；逗号本身居中对齐，然后1个空格；然后逗号之后的所有文本左对齐，不加空格。

### example 2

    abc,def,ghi
    a,b
    a,b,c

>  :Tabularize /,/r1c1l0

    abc , def, ghi
      a , b
      a , b  ,  c

注意：格式匹配重用了。相当于(以下用sp 表示 空格)
    
    r   1   c   1   l   0   r   1   c   1   l   0
    abe sp  ，  sp  def     ,   sp  ghi sp

即：第二个逗号右对齐，然后跟1个空格，文本居中对齐然后跟1个空格

### example 3

    abc,def,ghi
    a,b
    a,b,c

>  :Tabularize /^[^,]*\zs,/r0c0l0

    abc,def,ghi
      a,b
      a,b,c

模式匹配只使用一次，第二个逗号后面的就不管了。
这里使用了VIM的正则表达式

## 缺点

    a     b
    c d
假设a 与 b 中间有5个空格，对于tabular，没有办法把5个空格看成是1个空格，也就是无法对齐成下面的样子：
    
    a     b
    c     d

