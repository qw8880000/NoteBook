
## 注释

// to do

## 命名规则

### 通用命名规则

#### 选择一种命名规则

C程序标识符的命名是很自由的，并没有强制规范。但是团队协作编程时，还是需要统一规则，才能使代码优美，容易理解，维护简单。

常见的命名规则有：
* unix like  
    单词用小写字母，每个单词直接用下划线"_"分割，例如`text_mutex`，`kernel_text_address`。
* Windows风格(大驼峰法)   
    大小写字母混用，单词连在一起，每个单词首字母大写，如`OpenFile`，`MaxValue`。
* 小驼峰法  
    第一个单词以小写字母开始；第二个单词的首字母大写或每一个单词的首字母都采用大写字母，例如：`myFirstName`、`myLastName`。
* 匈牙利命名法  
    匈牙利命名法的变量名由一个或多个小写字母开始，这些字母有助于记忆变量的类型和用途，紧跟着的就是程序员选择的任何名称。
    这个后半部分的首字母可以大写，以区别前面的类型指示字母。而在最前面加入前缀`m_,s_,g_`表示变量的作用域类型。

命名规则各有优缺点，选用其中的一种，并执行下去即可。我个人比较钟爱unix like的风格。

#### 除了常见的通用缩写以外，不使用单词缩写，不得使用汉语拼音

说明：较短的单词可通过去掉“元音”形成缩写，较长的单词可取单词的头几个字母形成缩写，一些单词有大家公认的缩写，常用单词的缩写必须统一。
协议中的单词的缩写与协议保持一致。对于某个系统使用的专用缩写应该在注视或者某处做统一说明。

示例：一些常见可以缩写的例子：
```
argument 可缩写为 arg
buffer 可缩写为 buff
clock 可缩写为 clk
command 可缩写为 cmd
compare 可缩写为 cmp
configuration 可缩写为 cfg
device 可缩写为 dev
error 可缩写为 err
hexadecimal 可缩写为 hex
increment 可缩写为 inc、
initialize 可缩写为 init
maximum 可缩写为 max
message 可缩写为 msg
minimum 可缩写为 min
parameter 可缩写为 para
previous 可缩写为 prev
register 可缩写为 reg
semaphore 可缩写为 sem
statistic 可缩写为 stat
synchronize 可缩写为 sync
temp 可缩写为 tmp
```

#### 用正确的反义词组命名具有互斥意义的变量或相反动作的函数等

示例：
```
add/remove begin/end create/destroy
insert/delete first/last get/release
increment/decrement put/get add/delete
lock/unlock open/close min/max
old/new start/stop next/previous
source/target show/hide send/receive
source/destination copy/paste up/down
```

### 变量命名规则

* 全局变量应增加`g_`前缀
* 静态变量应增加`s_`前缀

首先，全局变量十分危险，通过前缀使得全局变量更加醒目，促使开发人员对这些变量的使用更加小心。
其次，从根本上说，应当尽量不使用全局变量。

* 禁止使用单字节命名变量，但允许定义i、j、k作为局部循环变量.
* 使用名词或者形容词＋名词方式命名变量

### 函数命名规则

* 函数命名应以函数要执行的动作命名，一般采用动词或者动词＋名词的结构

### 宏的命名规则

* 建议采用全大写字母，单词之间加下划线`_`的方式命名
* 除了头文件或编译开关等特殊标识定义，宏定义不能使用下划线`_`开头和结尾

### 枚举的命名规则

* 建议采用全大写字母，单词之间加下划线`_`的方式命名


## 函数设计

### 函数返回值

函数的返回值的意义可以分为以下种类：
* 正确与错误
* 是与否
* 某个对象
* 无返回值

**正确与错误**

某一类函数是用来执行一项操作或命令，这一类函数需要返回操作的结果。
一般linux程序员的习惯是：0 表示绝对正确，负数表示错误类型。

为什么函数默认使用0来表示正确可以参考：
//todo

例如：`int something_init(void)`

**是与非**

此类函数的返回值可以看成是布尔型，不是true就是false，只能两种状态。
而一般用：1 表示true，0表示false。

例如：`int isdigit(int c)`
此函数用来判断参数`c`是否是数字，返回1表示是数字，返回0表示不是。

**某个对象**

有时候函数原本不需要返回值，但为了增加灵活性如支持链式表达，

如：`char *strcpy(char *dest，const char *src);`

此函数表示把`src`字符串拼接到`dest`字符串上，它的返回值其实也是`dest`，
但是我们要这样理解：这是一种面向对象的方式，返回值指向对象`dest`，这样做可以增加灵活性，如链式表达：

```
char str[20];
int length = strlen( strcpy(str, "Hello World") );
```

**无返回值**

无返回值，那么声明为void返回类型。

