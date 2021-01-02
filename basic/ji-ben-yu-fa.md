# 控制执行流程

## 三大基础结构

顺序，选择、循环

## 判断结构

### 逻辑表达式

逻辑表达式是指其运算结果可以表示 true、false 的表达式。

{% hint style="success" %}
对某些语言而言，逻辑表达式并不要求返回 true、false，只要返回任何可以视为 true、false 的值即可。比如 C 语言中将非 0 值视为 true，0 视为 false。这种做法有时能很方便地写出简洁的代码，但也容易导致错误。Java 强制要求逻辑表达式返回布尔值能够避免这些问题。

比如，C++ 支持以下写法，而如果程序员实际希望比较 x 与 y 是否相等，这种误写可能导致死循环，且难以发现（编译器不会提示）：

```cpp
while(x = y) {
  // statement
}
```
{% endhint %}



### if-else 语句

if-else 是控制程序流程的最基本形式，其中 else 可选的，由 **程序语句（statement）**和 **布尔表达式（bolean-expression）**组成，其基本格式为：

```java
if bolean-expression)
  statement
else
  statement
```

{% hint style="info" %}
**短路求值：**详见 _基本运算 - 逻辑操作符_ 章节。
{% endhint %}

#### 

### switch 语句

switch 用于多路分支判断，由选择因子（integral-selector）和值（integral-value1）组成，基本格式为：

```java
switch(integral-selector) {
  case integral-value1: statement; break;
  case integral-value2: statement; break;
  // ...
  default: statement;
}
```

{% hint style="success" %}
switch 支持：Java 1.5 后支持枚举（Enum），1.7 后支持字符串（String）
{% endhint %}

{% hint style="warning" %}
**待修正：**这里的语句基本格式来自《Java 编程思想（第四版）》当时选择因子只支持整数值（或可转换为整数的值），因此名为 `integral`，待未来修正。
{% endhint %}



#### 直落（fall-through）

Switch 语句并非简单的多路分支，更合理的解释是将它当做跳转表，switch 语句在执行时，如果 case 语句内没有 break，它将继续执行下一个 case 内的代码，直到遇到 break 才会跳出。

{% hint style="info" %}
直落在使用时有一定危险，在某些时候有特别的用途，能够简化代码。但绝大数时候我们都只是希望实现多路分支，应该尽量不用这种特征，保证每个 case 都包含 break 语句。在某些代码检查工具中，默认对直落行为告警，如 TSLint：[https://palantir.github.io/tslint/rules/no-switch-case-fall-through/](https://palantir.github.io/tslint/rules/no-switch-case-fall-through/)，如果担心忘记，可以使用这些工具提醒。
{% endhint %}

{% hint style="success" %}
并不是所有语言都需要 break 命令跳出 switch 判断，在某些语言中，switch-case（或when-case）语句是自动 break 的，它只会执行所在 case 内的代码。

一般认为，这种设计来自于 C 语言，进一步地说是来自汇编语言的跳转特征，在当时这是常见的编程技巧。具体来说，在编译 switch-case 时，其判断代码统一在最前面，case 中的命令则被编译为连续的语句，根据判断结果跳转到执行位置，再将下面的所有代码全部执行。就这种设计而言，switch-case-fall-through 是很正常的体现。

关于编译时发生了什么，可参考：[https://blog.csdn.net/elim168/article/details/73732101](https://blog.csdn.net/elim168/article/details/73732101)
{% endhint %}

### 

## 迭代

### 基本迭代格式

Java 支持以下迭代语句：while，do-while 和 for。迭代由 **迭代语句（statement）**和 **布尔表达式（bolean-expression）**组成，其基本格式为：

* while 语句

```java
while(bolean-expression)
  statement
```

* do-while 语句

```java
do
  statement
while(bolean-expression)
```

* for 语句：额外具有 **初始化表达式（initialization）**和 **步进（step）**结构

```java
for(initialization; bolean-expression; step)
  statement
```



{% hint style="success" %}
**逗号操作符：**Java 唯一使用逗号操作符的位置就是 for 循环的控制表达式，其初始化和步进部分，支持使用用逗号分隔的语句，且这些语句均独立执行。（注意与逗号分隔符区分，它用于分隔参数不同参数）

在 C/C++ 等语言中，逗号操作符除了分隔不同语句，还会将将最后一个语句的值作为返回值。也有些人为了区分，将支持返回值的情况称为逗号运算符。

拓展参考：[逗号操作符](https://en.wikipedia.org/wiki/Comma_operator)**，**[JavaScript 中的逗号操作符](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comma_Operator)
{% endhint %}



### For-each 语法

for-each 语句适用于任何 Iterable 对象。



## 程序控制关键字

Java 支持以下无条件分支关键字：`return`，`break`，`continue`。

Java 不支持 goto 语句，但使用了 goto 中的 **标签**，以支持语句跳跃。

