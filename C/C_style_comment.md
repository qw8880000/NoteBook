
注释
------------------------

C 语言的注释符为 `/*…*/`

* **单条语句的注释，放在语句右边**

示例：
```
#define MAX_ACT_TASK_NUMBER 1000    /* active statistic task number */
```

* **代码块的注释，放在代码块上方**

```
/* Divide result by two, taking into account that x contains the carry from the add. */
for (int i = 0; i < result->size(); i++)
{
    x = (x << 8) + (*result)[i];
    (*result)[i] = x >> 1;
    x &= 1;
}
```

