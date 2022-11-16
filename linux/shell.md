
# 学习资料

  - [高级Bash脚本编程指南](http://www.linuxplus.org/kb/special-chars.html)
  - [快乐的linux命令行](http://billie66.github.io/TLCL/index.html)

# 如何在命令行中快速移动

```
CTRL + U -剪切光标前的内容
CTRL + K -剪切光标至行末的内容
CTRL + W -剪切光标后一个单词
CTRL + Y -粘贴
CTRL + E -移动光标到行末
CTRL + A -移动光标到行首
ALT + F -跳向下一个空格
ALT + B -跳回上一个空格
ALT + Backspace -删除前一个单词
Shift + Insert -向终端内粘贴文本
```

# awk

- [awk教程 - w3cschool](https://www.w3cschool.cn/awk/)

# 如何从管道里读取数据

方法一：可以通过read来读取
```sh
read LINE
while [[ ! -z $LINE ]]
do
    read LINE
done
```

方法二：使用xargs命令
```sh
ls | xargs myscript
```

方法三：从/dev/stdin读取（上一个命令的数据好像是输出到了stdin）
```sh
 info=$(cat </dev/stdin)
```

# xargs

管道实现的是将前面的stdout作为后面的stdin，但是有些命令不接受管道的传递方式，最常见的就是ls命令。有些时候命令希望管道传递的是参数，但是直接用管道有时无法传递到命令的参数位，这时候需要xargs，xargs实现的是将管道传输过来的stdin进行处理然后传递到命令的参数位上。也就是说xargs完成了两个行为：处理管道传输过来的stdin；将处理后的传递到正确的位置上。

- [xargs原理剖析及用法详解](https://www.cnblogs.com/f-ck-need-u/p/5925923.html)

# example

## 统计代码行数

命令：
  - `find . -name '*.c' | xargs wc -l {}`
  - `find . -name "*.[ch]*" | xargs wc -l | grep "total" | awk '{ print $1}'`

工具：
  - cloc
