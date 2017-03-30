
## 注释

+ **优秀的代码可以自我解释，不通过注释即可轻易读懂** 

+ **注释的目的是解释代码的目的、功能和采用的方法，提供代码难以直接表达的意图，而不是重复描述代码。**

如下注释属于多余：
```
++i; /* increment i */
if (receive_flag) /* if receive_flag is TRUE */
```

而如下的注释则给出了有用的信息：
```
/*  由于xx编号网上问题，在xx情况下，芯片可能存在写错误，此芯片进行写操作后，必须进行回读校
验，如果回读不正确，需要再重复写-回读操作，最多重复三次，这样可以解决绝大多数网上应用时的
写错误问题*/
int time = 0;
do 
{
write_reg(some_addr, value);
time++;
} while ((read_reg(some_addr) != value) && (time < 3));
```

+ **修改代码时，维护代码周边的所有注释，以保证注释与代码的一致性。不再有用的注释要删除。**

+ **文件头部应进行注释，注释必须列出：版权说明、版本号、生成日期、作者姓名、工号、内容、功能说明、与其它文件的关系、修改日志等，头文件的注释中还应有函数功能简要说明。**

例如：
```
/* --------------------------------------------------------------------------*/
/* * 
 * @file ftk_button.c
 * @Brief  按钮控件
 * @author xxxx <xxxxx@126.com>
 * @version v1.0
 * @date 2017-03-29
 */
/* ----------------------------------------------------------------------------*/
```

+ **函数注释描述函数功能、性能及用法，包括输入和输出参数、函数返回值**

例如：
```
/* --------------------------------------------------------------------------*/
/**
 * @Brief   设置按钮点击时的回调函数
 *
 * @Param thiz      铵钮对象
 * @Param listener  点击时的回调函数
 *
 * @Returns         0： 成功
 *                  -1：失败
 */
/* ----------------------------------------------------------------------------*/
int button_set_clicked_listener(FtkWidget* thiz, FtkListener listener);
```

+ **单行代码的注释放在代码的右边**

`#define MAX_ACT_TASK_NUMBER 1000 /* active statistic task number */`

+ **多行代码的注释放在代码的上方，且与上方的代码用空行隔开**

```
/* sccp interface with sccp user primitive message name */
enum SCCP_USER_PRIMITIVE
{
N_UNITDATA_IND, /* sccp notify sccp user unit data come */
N_NOTICE_IND,  /* sccp notify user the No.7 network can not transmission this message */
N_UNITDATA_REQ, /* sccp user's unit data transmission request*/
};
```

+ **文件头、函数头、全局常量变量、类型定义的注释格式采用工具可识别的格式**

说明：采用工具可识别的注释格式，例如doxygen格式，方便工具导出注释形成帮助文档。
以doxygen格式为例，文件头，函数和全部变量的注释的示例如下：
文件头注释：
```
/** 
*  @file           （本文件的文件名eg：mib.h）
*  @brief          （本文件实现的功能的简述）
*  @version 1.1    （版本声明）
*  @author        （作者，eg：张三）  
*  @date          （文件创建日期，eg：2010年12月15日）
*/
```

函数头注释：
```
/**
*@ Description:向接收方发送SET请求
* @param req - 指向整个SNMP SET 请求报文.
* @param ind - 需要处理的subrequest 索引.
* @return 成功：SNMP_ERROR_SUCCESS，失败：SNMP_ERROR_COMITFAIL
*/
Int commit_set_request(Request *req, int ind);
```

全局变量注释：
```
/**  模拟的Agent MIB */
agentpp_simulation_mib * g_agtSimMib;
```

函数头注释建议写到声明处。并非所有函数都必须写注释，建议针对这样的函数写注释：重要的、复
杂的函数，提供外部使用的接口函数。

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

### 参数的书写要完整，不要贪图省事只写参数的类型而省略参数名字。如果函数没有参数，则用void 填充。

```
void SetValue(int width, int height); // 良好的风格
void SetValue(int, int); // 不良的风格
float GetValue(void); // 良好的风格
float GetValue(); // 不良的风格
```

### 参数命名要恰当，顺序要合理

参数的设计本没有规则，只是前人的代码多了，慢慢出现了一些潜规则。

如 //dest src

### 避免函数有太多的参数，最多不能超过5个。

### 如果参数是指针，且仅作输入用，则应在类型前加const，以防止该指针在函数体内被意外修改。

### 函数参数合法性判断

即要判断合法性，又要防止过度判断，代码才会健壮又简洁。

// todo


