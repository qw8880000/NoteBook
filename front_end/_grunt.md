
# 源头资料

* [grunt](https://gruntjs.com/)

# 基础教程

* [grunt 中文网](http://www.gruntjs.net/)

# 常见问题

* grunt-usemin 无法替换index.html里的 blocks

原因：index.html里的换行是'^M'，可能影响了usemin任务。
解决：替换index.html里的'^M'结尾为'unix'下的换行。
