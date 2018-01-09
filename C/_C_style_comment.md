
> 作者：nicer  
> 微信公众号：好好编程

C风格要素之 注释
===============================

C 语言的注释符为 `/*…*/`。注释通常用于：

* 版权、文件声明；
* 函数接口说明；
* 代码行为或代码块功能提示。

优秀的代码可以自注释，就是不需要注释就可以理解它的意思。
我们的目标是写不需要注释的代码，但是在我们还没达到这种程序之前，还是要先学会写好注释。

注释原则
------------------------

* __在代码的功能、意图层次上进行注释，而不是重复描述代码__

示例：如下注释纯属多余。
```
++i;                /* increment i */
if (receive_flag)   /* if receive_flag is TRUE */
```

* __修改代码时，维护代码周围的注释，保证代码与注释的一致性__

* __避免在注释中使用缩写，除非是业界通用或子系统内标准化的缩写__

* __避免在一行代码或表达式的中间插入注释__

* __单条语句的注释，放在语句右边__

示例：
```
#define MAX_ACT_TASK_NUMBER 1000    /* active statistic task number */
```

* __代码块的注释，放在代码块上方__

```
/* Divide result by two, taking into account that x contains the carry from the add. */
for (int i = 0; i < result->size(); i++)
{
    x = (x << 8) + (*result)[i];
    (*result)[i] = x >> 1;
    x &= 1;
}
```

* __文件头、函数注释应该采用工具可识别的注释格式，方便工具导出注释形成帮助文档。__

doxygen格式格式的使用很广泛，建议使用。

文件头注释一般包括：

* 版权声明
* 作者
* 生成日期
* 文件说明
* 版本号
* 历史修改记录

函数注释则一般包括：

* 函数功能
* 返回值说明
* 参数说明

文件头注释示例：
```
/*
 * Copyright (c) 2009 - 2010  xxxWang <xxxWang@hotmail.com>
 *
 * Licensed under the Academic Free License version 2.1
 *
 * File:    widget.c    
 * Author:  xxxWang <xxxWang@hotmail.com>
 * Brief:   manage the widget state
 * Version: v1.0.0
 * History:
 * ================================================================
 * 2009-10-03 xxxWang <xxxWang@hotmail.com> created
 *
 */
```

函数注释示例：
```
/**
 * @Brief       判断文件是否存在
 *
 * @Param file: 需要判断的文件的全路径
 *
 * @Returns   1: 存在
 *            0: 不存在
 */
int is_file_exist(const char* file)                                                                                                                                             
{
    if(access(file, F_OK) == 0)
    { 
        return 1;  
    }   
    else 
    {
        return 0;  
    }   
}
```

