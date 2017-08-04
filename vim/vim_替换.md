
### vim 替换

     Vim替换命令的格式一般为（方括号中的内容为可选项，花括号中的内容为必选项）：

     :[range]s/{pattern}/{string}/[flag]

     ':'是这一类命令的开始；
     [range]表示命令的作用域，即命令起作用的行的范围；
     s是替换命令substitute的简写；
     {pattern}和{string}分别为待搜索的模式串和所要替换成的替换串；
     '/'用来界定{pattern}和{string}的起始；
     [flag]表示标志位，用来开启或关闭一些选项

     [flag]
     c confirm，每次替換前會詢問。
     e 不顯示 error。
     g globe，不詢問，整行替換。
     i ignore 不分大小寫。


     例子：

     82,90s/haha/hehe/
          82行到90行的haha替换成hehe

     可以使用 # 作为分隔符，此时中间出现的 / 不会作为分隔符

### VIM 插入
     
     vim搜索到pattern，如何在匹配到的文本后追加字符

     原字符串：module BUFX2 (Y, A, VDD, VSS); 
     期望：module BUFX2M (Y, A, VDD, VSS); 

     实现：%s/^\(module\s\w\+\)/\1M/g 

     pattern用\(\)括起来就是grouping的意思，用vim的术语来说就是atom。详细可查询:help atom，或直接:help \(也行

