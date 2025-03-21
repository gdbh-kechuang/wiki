---
title: 通识语法
description: 
published: true
date: 2025-03-21T06:01:14.282Z
tags: c/c++, python, basic
editor: markdown
dateCreated: 2025-03-21T06:01:14.282Z
---

本部分讨论语法规则，介绍编程语言的形式符号背後共通的思想， **避免每次新学一门编程语言都在重复的语法知识点上浪费精力。** 本文的内容使用 C/C++、Python 等主流编程语言讨论语法知识，以便观察这些形式语言背後的共性，具体的语法细节不加赘述。

文章内容多数不分先後，按需阅读即可。

> 你可能需要先至少了解一门编程语言，才能更好地理解文章内容
> {.is-info}

> 文章内容不完整，还待更新

## 基本

### 注释

注释（comment）是写在源代码里供人类阅读的内容，多用作解释代码、注意事项之类的。可以单独一行，也能跟在一般语句的後面。

常见的符号有： `//` 、 `#` 、 `/**/`

```python
# hello.py

print('hello from python!')     # 输出一句“hello!”
```

多行的注释。

```c
// hello.c

/*
这是一个多行注释
你可以
在这里
面先任何你想
要的说明信
息。
 */
```

### 语句终止符

许多语言使用分号 `;` 作为一句的结束标记。

```c
// directive.c

/* 定义一个函数，计算两个数的和 */
int add(int a, int b) {
    return a + b;
}
```

也有语言使用换行、缩进整顿语句。

```python
# directive.py

def multiplication_table(n):
    for i in range(1, n + 1):
        for j in range(1, n + 1):
            product = i * j
            print(f"{product}", end=' ')
        print()
```

## 运算符

常见的运算符：

-   算数：加减乘除、取模
-   比较：大于、小于、等于、不等于
-   逻辑：与或非
-   位运算：位与、位或、位非、位异或、位取反、移位
-   自增、自减
-   引用、解引用

有些语言的运算优先级可能和数学的运算优先级不一样，但是无需强行记忆，不确定的话多加一层括号就得了。

> 更多运算，参考各语言的数学标准库等等
> {.is-info}

### 转义符

转义符（escape character）用于在**字符串**里表示一些通常情况打不出来的特殊字符，一般是针对于系统控制字符。

最常见的是 ASCII 的“反斜杠加字符”转义风格，详见[完整 ASCII 码表](https://www.ascii-code.com/ASCII)。

```cpp
// esc.cpp

std::cout << "後面是一个换行符\n";
std::cout << "这有一个制表符\t前有一个制表符";
std::cout << "这样子打一个反斜杠\\";
std::cout << "\"打一对双引号\"";
std::cout << "一个单引号\'";
```

### 字面量

字面量（literal）是各种数据的“具体存在”，可以直接使用、给变量[赋值](#创建变量)：

```go
// literal.go

a := 42; // 42 是数字字面量
b := "42"; // "42" 是字符串字面量
fmt.Println("greetings!"); // "greetings!" 是字符串字面量
```

### 修饰符

> 还没写……

## 表达式、语句

> 还没写……

## 数据管理

想要管理数据，就需要使用若干内存（memory）空间把数据保存起来。保存起来的数据本质都是二进制了，因此需要一些操作才能正确地辨别、管理数据。

### 标识符

每个保存了数据的内存空间要有一个名字——标识符（identifier），这样就能被计算机正确辨识出那片内存空间。

标识符的命名自由，但并不完全任意，常见的约束有：

-   不得使用关键字（keyword），这些是编程语言保留用作语法的符号；
-   不得带有特殊符号，如空白符 ` ` 、百分符号 `%` 、哈希符号 `#` 等等；
-   不得以数字开头；
-   不得超出长度限制。

下面是合法的标识符：

```text
abc
minus45
getNum
fetch_bms_table
_area
qwertyuioipoasdfghjkjlkzxcvbnmn
```

下面是不合法的标识符：

```text
1second
#teshuzifu
her requiem
;w;
```

这些是……呃……是合法的标识符：

> 大多现代编程语言都支持用 ASCII 以外的字符做标识符，虽然一般都不建议。
> {.is-warning}

```text
übertragung
håndværker
说的道理
しょうひん

x̙͈̝̄͛̽̆͌́̕g̘̣̠̝̽͑͋̈̑̒͞q̛̤̦̝͋̔̋͌͒̆̋̚͡f̋̀͌̅͠
```

### 创建变量

声明（declaration）是先定好一个标识符，为数据预留内存空间，此时里面的值可能是随机的，或是编程语言所规定好的默认值。赋值（assignment）则是将具体的数据放进标识符所管理的内存空间。

这样，我们就得到了一个变量（Variable），这是管理数据的最小单位。

```c
// variable.c

int x;      // 声明
x = 10;     // 赋值

int y = 20; // 或者写作一行
```

有些语言不允许单单的声明，一定要赋具体的值才能合法地创建变量。

```python
# variable.py

a = 250 # 声明一个变量a，不赋值会报错
```

### 数据类型

数字类的数据可以进行算数运算，这很合理；但是对于文本类的数据，数字类型的运算规则就不太有意义了。所以各种数据需要区分以不同的数据类型（Data type），对不同数据采用不同的处理规则和运算规则。

有些语言在声明的时候，标识符旁边会有`int`、`float`之类的字眼，这种就是“类型[修饰符](#修饰符)”，指明该变量存储的是什么数据类型的数据。

显式地指明数据类型不是所有语言都需要或支持的，这取决于这门语言是**强类型**还是**弱类型**。

弱类型语言允许变量的类型在声明时不确定、後续允许改变类型；

```javascript
// datatype.js

let dynamicVar; // 声明一个变量
dynamicVar = "hello"; // 字符串类型
dynamicVar = 233; // 现在是数值类型
```

强类型语言的变量类型在声明时就被确定，且後续不能再变。

```cs
// datatype.cs

string staticVar = "233" // 定义字符串变量
staticVar = 233 // 爆！不能再赋值其他类型
/* Cannot implicitly convert type 'string' to 'int' */
```

### 基本数据类型

又称*原始数据类型*，一个基本数据类型的变量，同时只能存储一个这一种类型的数据。

> 基本数据类型不统一，各语言有各自定义的基本数据类型。具体参考对应语言的文档。譬如，Python 的数字类型分为`int`、`float`、`bool`和`complex`；而 Lua 将所有的数字都视为浮点数。

### 复合数据类型

一种复合数据类型（Composite data type）可以同时存储多个、多种基本数据类型的数据，并且还可以**自定义处理、运算规则**。

即使是像数组、指针这样的数据类型，本质上也是由基本数据类型和自定义处理规则所组合出来的。

使用标准库或第三方库提供的复合数据类型：

```python
# composite_data_type.py

# 用一个字典储存三条数据
temperature_sensors = {
    "sensor1": [22.5, 23.0, 21.8],
    "sensor2": [20.5, 21.0, 19.8],
    "sensor3": [25.0, 24.5, 26.0]
}

# 使用dict类型自有的运算规则，添加一条数据
temperature_sensors["sensor4"] = [22.5, 23.0, 21.8]
```

或者，根据需求自定义复合数据类型：

```c
// composite_data_type.c

// 使用结构体自定义一个叫做 sensor_t 的数据类型
struct sensor_t {
    const char* name;
    double data;
};

// 声明并赋值一个 sensor_t 类型的变量
sensor_t my_sensor = {
    name = "sensor_0",
    data = 25.9
};
```

> 发展成熟的语言，会通过复合数据类型提供很多实用且常用的数据结构。善用这些工具，避免被繁多的细节所淹没。
> {.is-info}

### 指针、引用

指针（pointer）也是一类复合数据类型，许多不接近底层的语言不直接提供这种数据类型。

指针存储的数据是**内存地址**，占用的内存空间大小通常只与机器位宽相关。譬如，64 位的计算机，一个指针占用 8 字节（8\*8byte=64bit）；而 16 位计算机的指针只占用 2 字节。

指针类型的变量须匹配对应的基本数据类型，这是为了确保解引用（dereferencing）——获取对应内存地址上的数据时，避免因类型不一致导致的错误或未定义行为。

```cpp
// pointer.cpp

#include <cstdint>

int32_t a = 0;          // 一个32位整型变量
int32_t* pa = &a;    // 指针变量da存储a的地址
int32_t da = *pa;  // 解引用pa，把a的值赋值给da
```

引用（reference）相当于给变量再取了一个别名，对引用进行的所有操作等效于直接对该变量操作。

引用存储的也是内存地址，但并不占用空间。引用一旦赋值就跟那个变量绑定，不可再更改，只有变量被销毁，引用才随之销毁。

```cpp
// reference.cpp

#include <string>

string b = "www";
string& rb = b;
rb = "mmm";      // b存储的值会相应改变
```

### 类型转换

不同的数据类型因不同的处理规则而无法进行运算。不过，语言的设计者也考虑了不同数据类型之间运算的合理之处。比如整数和浮点数相加，这应该是理所应当的。

因此，就有了类型转换（Type Conversion）这一机制。给不同数据类型之间定义了转换规则，如果两数据类型能够合理地运算，则将其中一种数据类型**隐式**类型转换（Implicit ~）为相同类型，再应用相同数据类型的运算规则。

```cpp
// implicit.cpp
float a = 3.0
int b = 13
auto c = a + b  // 结果是浮点型 16.0
```

```python
# implicit.py

s = "1 + 1 = "
n = 10
r = s + n # 数字变量 n 被隐式转换成字符串变量，随後和 s 进行字符串拼接
print(r)  # 输出: "1 + 1 = 10"
```

当然，这种有限的提前定义好的转换规则不可能覆盖无限的情况，尤其对于自定义的数据类型。此时可以通过**显式**类型转换（Explicit ~）把数据转换成期望的数据类型。

```js
// explicit.js

const dateString = prompt(); // 由用户输入的字符串
const past = Date.parse(dateString); // 字符串转换为时间戳
const present = new Date().getTime(); // 当前时间的时间戳
const elapse = present - past; // 两时间戳相减
```

## 流程控制

### 分支结构

分支结构会根据表达式的值，决定执行哪些语句块。

`if-else` 语句中，每次只会有一项语句块的代码被执行。

```c
// if_else.c

if (a > 30) {
    puts("big a");
}
// 上面的表达式为假时，才会继续往下
else if (a < 15) {
    puts("small a");
}
else if (a == -1) {
    puts("bad a");
}
// 以上所有表达式都为假时，才会执行else的语句块
else {
    puts("middle a");
}
```

`switch` 语句对传入的值进行判断，如果能对应上`case`的条件，就会执行对应的语句块。

```cpp
// switch.cpp

#include <iostream>

switch (x) {
    case 1:
        std::cout << "x is 1" << std::endl;
        break;
    case 2:
        std::cout << "x is 2" << std::endl;
        break;
    case 3:
        std::cout << "x is 3" << std::endl;
        break;
    case 4:
        std::cout << "x is 4" << std::endl;
        break;
    // 以上case全都不满足，才会执行default的代码块
    default:
        std::cout << "x is x" << std::endl;
        break;
}
```

### 循环结构

`for` 三段式是循环语句最最常见的语法形式。一条 for 语句可接受三个表达式：

-   **初始化循环变量**：定义若干存在于循环期间的变量，循环结束后销毁
-   **结束表达式**：表达式的值为假，就结束这个 for 语句
-   **迭代表达式**：当前循环结束后执行该表达式

```c
// for_loop.c

// 初始化一个变量 i；i大于等于10结束；每次迭代後i自增
for (int i=0; i<10; i++) {
    // 打印当前 i 的值
    puts(i);
}
```

> 三个表达式都可以为空，等价于 while 循环语句

`while` 循环只有一个结束表达式。while 会一直循环到表达式为假。

```c
// while_loop.c

int i = 100;
while (i) {
    i--;
}
```

还有一种，迭代器（Iterator）循环。迭代器是一些数据结构自带的东西，提供一种访问数据结构内部元素的方法，而无需暴露其内部结构。

> 迭代器是比较现代语言的特性，较老的语言一般不支持

```python
# iterator_loop.py

# range(3) 的本质是生成了一个列表[0,1,2]
# 每次循环，循环变量 i 获取到迭代器的值
for i in range(3):
    print(i)

# 同理，两个循环变量每次获取迭代器的内容
a = {
    'n1':3,
    'n2':2,
    'n3':1
}
for i,j in a.items():
    print(i,j)
```

## 代码结构

### 函数

函数（Function）可以把代码块打包起来，提供代码复用、减少工作量。

函数的常见语法形式：

```c
// function.c

int foo(int a, int b, int c){
    return a + b * c
}
```

-   函数名：这个函数的标识符
-   参数：执行该函数所需要的前提数据
    -   形式参数：参数的标识符，在函数体内使用
    -   实际参数：传入的具体数据
-   函数体：该函数所执行的具体代码块
-   返回值： 函数执行完毕返回的值

### 类

类（Class）是一种将数据和处理数据的方法**聚合在一起**，是一种面向对象编程(OOP, Object-Oriented Programming)的风格——以“生物遗传学”的思维方式来组织代码。

> 类和结构体一样，都用于创建新的[复合数据类型](#数据类型)

```python
# class.py

"""
    创建一个传感器的类
    这个类有一个数据 pos
    还有两个处理数据的方法 getPos 和 setPos
"""
class Sensor:
    pos = float()
    def getPos(self):
        print("data:", self.pos)
    def setPos(self, value):
        self.pos = value

# 创建一个 Sensor 类型的变量
my_sensor = Sensor()
# 使用setPos操纵数据
my_sensor.setPos(2.17800)
```

### 作用域、生命周期

作用域（Scope）指的是变量、函数等对象被定义和**能够被访问**的代码区域。整个程序都能访问到的，就是全局变量（Global Variables）。

生命周期（Lifecycle）指的是变量、函数等对象在内存中存在的时间，通常由语言的编译器或运行时环境管理，无需人类操心。生命周期通常和作用域相关。

> C 风格语法的语言中，常见用花括号 `{}` 控制变量的作用域和生命周期。花括号内，可访问所有当前作用域、所有上层作用域的对象。

![我有异域症](scope.webp)

上图中，变量 i 的生命周期从第一个花括号开始，作用域仅有当前花括号内；第一个花括号之後，i 的生命周期结束并且**被销毁**。
