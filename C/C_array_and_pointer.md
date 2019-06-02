---
title: 数组 | C语言
date: 2018-01-16 14:51:11
categories:
  - c语言
tags:
  - c语言
abbrlink: 15eba75861fd8959
---

# 数组

`int a[10]`中的a是数组名，它指向数组中的第一个元素。但是当其做为`sizeof`的操作数，或者使用`&`取地址的时候，要把`a`作为整个数组来考虑。

# 数组名与数组名取地址

先看一个例子：
```c
int a[10] = {0};
printf("%p, %p\n", a, &a);
```
打印结果是`0xbfc077b4, 0xbfc077b4`。两者的值是一样的，但是它们的类型不同。`a`表示的是数组第一个元素的地址，类型是`int*`，`&a`表示数组`a`的地址，类型是`int (*)[10]`，一个指向包含10个int元素数组的指针。

我们可以使用下例对上述结论进行验证：
```c
int b[10] = {0};
printf("%p, %p, %p, %p\n", b, &b, b+1, &b+1);
```
打印结果为`0xbf890214, 0xbf890214, 0xbf890218, 0xbf89023c`。`a+1`的步长是一个数组元素的大小，而`&a+1`的步长却是整个数组的大小。

# 数组当函数参数

数组当函数参数的时候，其类型退化为指针。来看一下例子：
```c
int test_func(int a[])
{
    printf("the value is %d\n", sizeof(a));
    return 0;
}
int main(int argc, char* argv[])
{
    int arr[10] = {0};
    test_func(arr);
    return 0;
}
```
上述例子中的`sizeof(a)`为4，因为数组当函数参数时，退化成指针，所以`sizeof(a)`其实是`sizeof(int*)`。
