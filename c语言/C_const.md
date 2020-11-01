# const 的定义

任何变量的声明都可以使用const限定符限定。该限定符指定变量的值不能被修改。对数组而言，const限定符指定数组所有元素的值都不能被修改。

例如：
```c
const double e = 2.71828182845905;
const char msg[] = "warning: ";

e = 3.14;       // 非法
msg[0] = 'a';   // 非法
```

const 也常用来修饰指针，表示指向区域的内容不能修改，例如：
```c
int arr[10] = {0};
const int* p_arr = arr;

arr[0] = 1;         // 合法
p_arr[0] = 1;       // 非法
```

# 常量指针 与 指针常量

常量指针，表示变量是指针，指向常量，即指针指向的内存区域不可被修改。
```c
int arr[10] = {0};
int arr_2[10] = {0};
const int* p_arr = arr;     // 声明常量指针

arr[0] = 1;         // 合法
p_arr[0] = 1;       // 非法
p_arr = arr_2;      // 合法
```

指针常量，表示变量是常量，变量本身的值不能被修改。
```c
int arr[10] = {0};
int arr_2[10] = {0};
int * const  p_arr = arr;     // 声明指针常量

arr[0] = 1;         // 合法
p_arr[0] = 1;       // 合法
p_arr = arr_2;      // 非法
```

