# java 对比 C/C++

## 全局变量

Java 程序中，不能在所有类之外定义全局变量，只能通过在一个类中定义公用、静态的变量来实现一个全局变量。Java 对全局变量进行了更好的封装。而在C 和C++中，依赖于不加封装的全局变量常常会造成系统的崩溃。

## Goto 语句

Java 不支持`c/c++`中的Goto 语句，而是通过异常处理语句try、catch、finally 等来代替`c/c++`中用Goto 来处理遇到错误时跳转的情况，使程序更可读且更结构化。

## 指针

指针是 `c/c++`中最灵活，也是最容易产生错误的数据类型。由指针所进行的内存地址操作常会造成不可预知的错误，同时通过指针对某个内存地址进行显示类型转换后，可以访问一个C++中的私有成员，从而破坏了安全性，造成系统的崩溃。
而Java 对指针进行完全的控制，程序员不能直接进行任何指针操作，例如，把整数转化为指针，或者通过指针释放某一内存地址等。同时，数组作为类在Java 中实现，很好地解决了数组访问越界这一在`c/c++`中不做检查的错误。

## 内存管理

在 C 中，程序员通过库函数`malloc( )`和`free( )`来分配和释放内存，`C++`中则通过运算符new 和delete 来分配和释放内存。再次释放已释放的内存块或未被分配的内存块，会造成系统的崩溃；同样，忘记释放不再使用的内存块也会逐渐耗尽系统资源。
而在Java 中，所有的数据结构都是对象，通过运算符new 为它们分配内存。通过 new 得到对象的处理权，而实际分配给对象的内存可能随程序运行而改变，Java 对此自动地进行管理并且进行垃圾收集，有效地防止了由于程序员的误操作而导致的错误，并且更好地利用了系统资源。

## 数据类型的支持

在 `c/c++`中，对于不同的平台，编译器为简单数据类型，如int、float 等分别分配不同长度的字节数，例如，int 在 IBM PC 中为16 位，在VAX-11 中为32 位，这导致了代码的不可移植性，但在Java 中，对于这些数据类型总是分配固定长度的位数，如对int 型，它总占32 位，这就保证了Java 的平台无关性。

## 类型转换

在 `c/c++`中，由于可以通过指针进行任意的类型转换，因此常常带来不安全性；而Java 中，系统在运行时对对象的处理要进行类型相容性检查，以防止不安全的转换。

## 头文件

`c/c++`中用头文件来声明类的原型及全局变量、库函数等，在大的系统中，维护这些头文件是很困难的。而Java 不支持头文件，类成员的类型和访问权限都封装在一个类中，运行时系统对访问进行控制，防止对私有成员的操作。同时，Java 中用import 语句来与其他类进行通信，以使用它们的方法。

## 结构和联合

`c/c++`中的结构和联合中所有成员均为公有，这就带来了安全性问题。Java 中不包含结构和联合，所有的内容都封装在类中。

## 预处理

`c/c++`中用宏定义来实现的代码给程序的可读性带来了困难。在Java 中，不支持宏，它通过关键字final 来声明一个常量，以实现宏定义中广泛使用的常量定义。

## static

在C语言中，static 用于修饰局部变量时，称为局部静态变量，通常是在某个函数体内，只能在该函数内被调用，它的值不会因为函数调用的结束而被清除，当函数再次被调用时，它的值是上一次调用结束后的值。当用于修饰全局变量时，称为静态全局变量，它可以被该文件内的所有函数访问，但不能被其它文件内的函数访问。当用于修饰函数时，称之为静态函数，静态函数的作用域仅限于本文件，不能被其它文件调用。
在JAVA中，static修饰的字段，称为静态字段，静态字段只有一个共享“空间”，所有实例都会共享该字段，与c语言的静态变量作用一样。对于静态字段，无论修改哪个实例的静态字段，效果都是一样的，所有实例的静态字段都被修改了，原因是静态字段并不属于实例，虽然实例可以访问静态字段，但是它们指向的其实都是Person class的静态字段。所以，所有实例共享一个静态字段。因此，不推荐用实例变量.静态字段去访问静态字段，因为在Java程序中，实例对象并没有静态字段。在代码中，实例对象能访问静态字段只是因为编译器可以根据实例类型自动转换为类名.静态字段来访问静态对象。推荐用类名来访问静态字段。可以把静态字段理解为描述class本身的字段（非实例字段）。
在JAVA中，用static修饰的方法称为静态方法，调用静态方法则不需要实例变量，通过类名就可以调用。静态方法类似其它编程语言的函数。