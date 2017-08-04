@Filename:       5.7 vim插件--cscope.md  
@Author:         wangjl  
@Date:           2015-11-02 10:57  
@Last modified:  2015-11-02 10:57  
@Description:   

## 参考

[vim+cscope](http://blog.csdn.net/dengxiayehu/article/details/6330200)

## cscope使用

cs find s xxxx

    0或者s   —— 查找这个C符号
    1或者g  —— 查找这个定义
    2或者d  —— 查找被这个函数调用的函数（们）
    3或者c  —— 查找调用这个函数的函数（们）
    4或者t   —— 查找这个字符串
    6或者e  —— 查找这个egrep匹配模式
    7或者f   —— 查找这个文件
    8或者i   —— 查找#include这个文件的文件（们）
    
