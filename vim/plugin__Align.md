@Filename:       plugin__Align.md  
@Author:         wangjl  
@Date:           2016-05-24 15:46  
@Last modified:  2016-05-24 15:46  
@Description:   

## align 

一个文本对齐插件

### example

        x= y= z= 3;
        xx= yy= zz= 4;
        zzz= yyy= zzz= 5;
        a= b= c= 3;

:AlignCtrl l
:1,4Align =

表示 左对齐 分隔符为 =

        x   = y   = z   = 3;
        xx  = yy  = zz  = 4;
        zzz = yyy = zzz = 5;
        a   = b   = c   = 3;

说明：
1.为什么每个等号前后都有一个空格？
是由于前后的字符默认为 p1P1(p1表示分隔符前面是一个空格，P1表示后面一个是空格)。
如果希望等号前后没有空格，只需要输入：
        :AlignCtrl lp0P0

### example

尽管一般的分隔符只有一个字符的长度，实际上它是通过正则表达式制定的。而且也可以左对齐，右对齐和居中对齐。
接入需要左-右-左-右对齐？很简单：
        :AlignCtrl lr
        :1,4Align =
这是因为对齐命令是循环的，例如上面的lr实际上等效于：
    lrlrlrlrlrlrlr...


