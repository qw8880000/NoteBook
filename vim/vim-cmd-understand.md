---
title: vim命令的理解
date: 2017-11-01 17:12:44
categories:
    - vim
tags:
    - vim
abbrlink: 0cb10c44a53e9e0c
---

这部分来源 [一起来说 Vim 语](http://www.jianshu.com/p/a361ce8c97bc)，理解此部分是需要你已经了解了 Vim 的几种常用的工作模式（正常模式、插入模式、命令模式等）
总结得很好，对于记忆vim命令非常有帮助，感谢。

## 动词

动词代表了我们打算对文本进行什么样的操作。例如：

```bash
d # 表示删除delete
r # 表示替换replace
c # 表示修改change
y # 表示复制yank
v # 表示选取visual select
```

## 名词

名词代表了我们即将处理的文本。Vim 中有一个专门的术语叫做 [文本对象] text object，下面是一些文本对象的示例：

```bash
w # 表示一个单词word
s # 表示一个句子sentence
p # 表示一个段落paragraph
t # 表示一个 HTML 标签tag
引号或者各种括号所包含的文本称作一个文本块。
```

## 介词

介词界定了待编辑文本的范围或者位置。

```bash
i # 表示在...之内 inside
a # 表示环绕... around
t # 表示到...位置前 to
f # 表示到...位置上 forward
```

## 数词

数词指定了待编辑文本对象的数量，从这个角度而言，数词也可以看作是一种介词。引入数词之后，文本编辑命令的语法就升级成了下面这样：

```
动词 介词/数词 名词
```

下面是几个例子：

```bash
c3w  # 修改三个单词：change three words
d2w  # 删除两个单词：delete two words
```

另外，数词也可以修饰动词，表示将操作执行 n 次。于是，我们又有了下面的语法：

```
数词 动词 名词
```

请看示例：

```bash
2dw # 两次删除单词（等价于删除两个单词）: twice delete word
3x  # 三次删除字符（等价于删除三个字符）：three times delete character
```

有了这些基本的语言元素，我们就可以着手构造一些简单的命令了。文本编辑命令的基本语法如下：

```
动词 介词 名词
```

下面是一些例子（如果熟悉了上面的概念，你将会看到这些例子非常容易理解），请亲自在 Vim 中试验一番。

```bash
dip # 删除一个段落: delete inside paragraph
vis # 选取一个句子: visual select inside sentence
ciw # 修改一个单词: change inside word
caw # 修改一个单词: change around word
dtx # 删除文本直到字符“x”（不包括字符“x”）: delete to x
dfx # 删除文本直到字符“x”（包括字符“x”）: delete forward x
```

