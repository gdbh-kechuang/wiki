---
title: "基本语法通识"
date: 2024-10-30T23:54:10+08:00
weight: 21
---

> 以下语法知识没有很强的关联，大多可以不分先後，挑不认识的看。

## 注释

注释（comment）是写在源代码里供人类阅读的内容，多用作解释代码原理、注意事项之类的。可以单独一行，也能跟在一般语句後面。

常见的符号有： `//` 、 `#` 、 `/**/`

```python {filename=python}
print('hello from python!')     # 输出一句 hello from python!
```

还有多行的注释。

```c {filename=c}
/*
这是一个多行注释
用于说明代码的功能和目的。
你可以
在这里
面添加任何你想
要的说明信
息。
 */
```

## 语句终止符

许多语言使用分号 `;` 作为一条语句的结束标记。有些语言可以省略终止符。

```c {filename=c}
// 定义一个函数，计算两个数的和
int add(int a, int b) {
    return a + b;
}
```

也有语言使用换行、缩进等方式整顿语句。

```python {filename=python}
def multiplication_table(n):
    for i in range(1, n + 1):
        for j in range(1, n + 1):
            product = i * j
            print(f"{product}", end=' ')
        print()
```

## 转义符

转义符（escape character）用于在**字符串**中表示一些控制字符或通常情况打不出来或无法使用的特殊字符。比如引号 `"`、反斜杠 `\`或保留字等等。

最常见的转义方式是ASCII的“反斜杠加一个符号”。

```cpp {filename=c}
puts("Hello, World!\n"); // 换行符
puts("This is a tab:\tTabbed text."); // 制表符
puts("Here is a backslash: \\"); // 反斜杠
puts("\"C++ is awesome tho!\""); // 双引号
puts("Single quote: \'"); // 单引号
```

## 修饰符

## 创建数据

### 标识符

计算机处理很多很多数据，这些数据需要占用一定的内存空间，而这些空间需要有名字才能被正确识别，即标识符（identifier）。

标识符的命名很自由，但不能完全随便，许多语言都有这些限制：
- 不得使用保留字（Reserved word）——保留字是一门语言用作语法的字词、符号；
- 不得带有特殊符号，空白符 ` ` 、百分符号 `%` 、哈希符号 `#` 等等；
- 不得以数字开头；
- 不得超出长度限制。


这些是合法的标识符：
```text
abc
minus45
getNum
fetch_bms_table
_area
```

这些是不合法的标识符：
```text
1second
#teshuzifu
her requiem
```

> 大多现代编程语言都可以用拉丁字母以外的字符起名，但通常不建议。

这些……呃……是合法的标识符：
```text
håndværker
übertragung
说的道理
しょうひん

x̙͈̝̄͛̽̆͌́̕g̘̣̠̝̽͑͋̈̑̒͞q̛̤̦̝͋̔̋͌͒̆̋̚͡f̋̀͌̅͠
```

### 声明、定义、赋值

为了保存数据，我们需要声明（declaration）并定义（definition）一个[变量](#变量和字面量)。底层发生的事，就是申请了一片未使用的内存，这个变量就管理这片内存，数据就存在这里。

定义名为“x”和“y”的变量，分别把10和20赋值（assignment）给x和y：

```c {filename=c}
int x;      // 声明
x = 10;     // 定义

// 声明和定义可以写作一行。
int y = 20;
```

许多动态语言不明确区分声明和定义。声明即是定义，定义即是声明。

```python {filename=python}
# 声明并定义一个变量a，如果单写一个a会报错。
a = 'www'
```

### 变量和字面量

变量（variable）可以存储任何合法[数据类型](#数据类型)的数值。一般的声明定义语句所创建的就是变量。

字面量（literal）则是各种数据的具体表示。字面量可以直接使用，或者作为赋值给变量的目标：

```go {filename=go}
a := 42;
b := 'h';
fmt.Println("greetings!");
```

上述例子包含`42`数字字面量、`'h'`字符字面量，以及`"greetings!"`字符串字面量。

## 数据类型

数字类的数据可以进行算数运算，但是对于文本类的数据，给数字用的那套运算规则就没什么意义。所以各种数据就需要区分以不同的数据类型（Data type），对不同数据采用不同的处理规则。

有些语言在声明的时候需要在标识符附近带上`int`、`float`之类的[修饰符](##修饰符)，这就是指明该变量存储的是什么类型的数据。但不是所有语言都需要显式地指明类型，这取决于这门语言是**动态的**还是**静态的**。

动态语言的变量在编译、运行时能一定程度转换成其他类型；

```javascript {filename=javascript}
let dynamicVar = 'hello from js';    // 字符串类型
dynamicVar = 233;    // 现在是数值类型
```

静态语言的变量在编译、运行之前就确定了其类型，後续不能再变。

```kotlin {filename=kotlin}
var staticVar : Int = 233 // 定义了一个整型变量

staticVar = "233" // 爆！不能再赋值成其他类型
/* Assignment type mismatch: actual type is 'kotlin.String', but 'kotlin.Int' was expected. */
```

### 基本数据类型

或称*原始数据类型*，用于存储最简单、最基本的一类数据。

基本数据类型是没有统一的，各语言定义了各自的基本数据类型。例如Python的数字类型分为`int`、`bool`、`float`和`complex`；而Lua则将所有的数字都视为浮点数。

### 复合数据类型

由多个基本数据类型组合而成。一种复合数据类型可以存储多个值，并且这些值可以是不同的数据类型。

根据需求自定义的复合数据类型：

```c {filename=c}
// 定义新的sensor类型
struct sensor {
    const char* name;
    double data;
};

sensor sensor2 = {
    name = "www",
    data = 25.9
}; // 创建了一个sensor类型的变量
```

使用语言自身实现的复合数据类型，比如python的`list`和`dict`：

```python {filename=python}
# 用字典储存了三个传感器的数据
# 用列表记录每个传感器探测到的数值
temperature_sensors = {
    "sensor1": [22.5, 23.0, 21.8],
    "sensor2": [20.5, 21.0, 19.8],
    "sensor3": [25.0, 24.5, 26.0]
}
```

还有标准库或第三方库等等，提供更多常用的数据类型和数据结构。善用这些工具，避免重复的工作。

### 指针和引用

指针（pointer）是比较特殊的一类，许多不接近底层的语言没有直接提供这种数据类型。指针存贮的数据都是**内存地址**，其占用空间只与机器位宽相关。

指针类型的变量也区分类型，是为了确保**解引用**（dereferencing）时能正确获取到数据，避免因类型不匹配导致的错误和未定义行为。

```c {filename=c}
int32_t a = 0;          // 一个32位整型变量
int32_t* ptr_a = &a;    // 该指针存储a的地址
int32_t deref_a = *pa;  // 解引用ptr_a所存储的地址，获取到a的值并赋值给deref_a
```

引用（reference）可理解为给变量取了一个别名，对引用进行的所有操作等效于对该变量的操作。

```cpp {filename=cpp}
string b = "www";
string& ref_b = b;
ref_b = "mmm";      // b所存储的值会变
```

### 类型转换

## 基本运算符

> 有些语言的运算可能稍稍不符合数学直觉，但是也不需要去记忆，不确定的话多加一层括号就得了。

- 算数：加减乘除、取模（更多数学运算参考各语言的数学标准库）
- 比较：大于、小于、等于、不等于
- 逻辑：与或非
- 位运算：位与、位或、位非、位异或、位取反、移位
- 自增自减

## 流程控制：条件判断、循环结构

## 表达式、返回值、左值右值



## 函数

### 匿名函数

### 闭包

## 类和对象

## 生命周期、作用域

## 编译工具链


## 参考资料

[write-magic-code/public (github.com)](https://github.com/write-magic-code/public/blob/main/language/language.md)
