
> 作者：nicer  
> 微信公众号：好好编程

C风格要素之 程序的版式
==================================

程序的版式并不影响程序功能，但是它影响阅读。

我们的目标是使用代码结构清晰、整洁、漂亮。

程序标题
------------------------

注释
------------------------

合理使用空行
------------------------

* **函数体之间用空行分隔**

示例：
```
void *memset(void *s, int c, size_t n)
{
    ...
}

void *memcpy(void *dest, const void *src, size_t n)
{
    ...
}
```

* **不同功能的代码块之间用空行分隔**

示例：
```
int window_init(void)
{
    button.id = 1;
    button.width = 50;
    button.height = 100;

    text.id = 2;
    text.data = "hello";
}
```

总之，空行的使用原则是，把不同功能的代码块之间用空行分隔。

合理使用空格
------------------------

* **二元操作符两边使用空格**

示例
```
int a = 0;

a += b;

a = c + b;

if(a >= 2000)

if(a || b)

```

* **参数之间使用空格** 

示例：
```
void Func1(int x, int y, int z);
```

合理使用括号
------------------------

* **用括号分隔子表达式，不要只靠默认优先级来判断**

示例：
```
if((a && b) || (c && d))
```

* **建议：用括号分隔if/while/for等语句的代码块，那怕代码只有一行**

示例：
```
if(a > b)
{
    print("a is bigger than b\n");
}
```

合理使用缩进
------------------------

代码使用缩进的风格编写，每一级都正常缩进。缩进可以是tab也可以是4个空格，选用一种，不要两种都用。

示例：
```
if(a > b)
{
    for(i = 0; i < 100; i++)
    {
        ...
    }
}
```

长行拆分
------------------------

* **代码行最大长度宜控制在70 至80 个字符以内**

示例：
```
if ((very_longer_variable1 >= very_longer_variable12)
        && (very_longer_variable3 <= very_longer_variable14)
        && (very_longer_variable5 <= very_longer_variable16))
{
    dosomething();
}
```

修饰符的位置
------------------------

