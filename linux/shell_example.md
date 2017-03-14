
## 统计代码行数

命令：
* `find . -name '*.c' | xargs wc -l {}`
* `find . -name "*.[ch]*" | xargs wc -l | grep "total" | awk '{ print $1}'`

工具：
* cloc
