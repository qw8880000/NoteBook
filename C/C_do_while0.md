
`do{}while()`这个语法在C编程中我自己很少使用，直到有一天读到了李先静先生的《系统程序员成长计划》，发现了它还有这种使用方法。

**我们可以使用`do{}while(0)`来编写单进单出函数**。

在一些函数里，我们希望在函数的入口与出口处做一些配对的操作，比如内存的申请与释放、文件的打开与关闭、加锁与解锁等。在这样的函数里可以设计成单进单出，好处是后期维护不容易出错。

假设我们有一个函数，里面的操作存在竞争，那我们为它加上锁的机制，代码可能是这样：
```c
int data_process(const char* data)
{
    lock(mutex);

    // 异常判断1
    if(!condition1) {
        unlock(mutex);
        return -1;
    }

    // 异常判断2
    if(!condition2) {
        unlock(mutex);
        return -1;
    }

    data_convert(data);
    ...

    unlock(mutex);
    return 0;
}
```

上述函数的写法不是单进单出，即有很多出口，于是每个出口处都必须记得解锁。如果换成单进单出的写法，上述情况会变得简单一些，只需要记得在最后出口处解锁即可。
```c
int data_process(const char* data)
{
    int ret = -1;
    lock(mutex);

    // do{}while(0) 函数体内不允许使用return
    do {
        // 异常判断1
        if(!condition1) {
            ret = -1;
            break;
        }

        // 异常判断2
        if(!condition2) {
            ret = -1;
            break;
        }

        data_convert(data);
        ...
        ret = 0;

    } while(0);

    unlock(mutex);
    return ret;
}
```

改进后的代码只需要记得不要在`do{}while(0)`代码块里使用`return`，而原先的代码需要在每一个`return`处检查是否解锁。个人认为还是`do{}while(0)`方法比较好记，而且当团队里的成员对`do{}while(0)`的用法熟悉了以后，一但看到此结构出现便可以条件反射般的意识到此函数有机关，使用`return`需谨慎。

# 更多

* [C语言汇总](http://blog.wangjinle.com/posts/53291f7288071263.html)
