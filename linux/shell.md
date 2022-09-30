
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

# example

## 统计代码行数

命令：
  - `find . -name '*.c' | xargs wc -l {}`
  - `find . -name "*.[ch]*" | xargs wc -l | grep "total" | awk '{ print $1}'`

工具：
  - cloc
