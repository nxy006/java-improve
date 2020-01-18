# 控制执行流程

## 三大基础结构

顺序，选择、循环

## 判断结构

### 逻辑表达式

逻辑表达式是指其运算结果可以表示 true、false 的表达式。

{% hint style="success" %}
对某些语言而言，逻辑表达式并不要求返回 true、false，只要返回任何可以视为 true、false 的值即可。比如 C 语言中将非 0 值视为 true，0 视为 false。这种做法有时能很方便地写出简洁的代码，但也容易导致错误。Java 强制要求逻辑表达式返回布尔值能够避免这些问题。
{% endhint %}

{% hint style="warning" %}
计划增加一个在 C 语言中使用非 true/false 用于逻辑判断时容易出错的例子。
{% endhint %}



#### 短路求值（Short-circuit evaluation）

逻辑表达式的短路求值在编程语言中普遍存在，指的是运算表达式时如果发现整个表达式的结果已经可以运算得到，就不再继续运算的特点。

{% hint style="info" %}
在编程中要注意短路求值问题，需要执行的代码不要放入逻辑表达式，即便能够保证它按期望执行也不应该这么做，其他人的轻微改动就可能破坏其正常功能，除非表达式真的非常非常易懂。
{% endhint %}

{% hint style="success" %}
对有些语言而言，除了短路求值，它还提供了非短路求值的方式，比如 Java、C\#、Ruby 都可以使用逻辑运算符替代逻辑运算符，此时将对每个子表达式均求值。常见的逻辑运算符一般包括：&（与）、`|`（或）、`!`/`~`（非）、`^`（异或）。（注：Java 使用`~`表达非。）

对另一些语言，则只提供了短路求值的写法，如果需要非短路求值，只能采用变通的写法，先求出每个子表达式的值，再将其这些用于逻辑判断。比如 C/C++。
{% endhint %}

例题：[牛客网](https://www.nowcoder.com/questionTerminal/8cf208348b5b42a6b509b164efec3cc7)

### 

### Switch - case 判断语句



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

### 三元操作符

三元操作符指可以对三个参数执行操作的运算符，在 Java 只有一种三元运算符，即： `? :`



#### 三元操作符的类型转换规则

1. 若两个操作数不可转换，则不做转换，返回值为Object类型
2. 若两个操作数是明确类型的表达式（比如变量），则按照正常的二进制数字来转换，int类型转换为long类型，long类型转换为float类型等。 
3. 若两个操作数中有一个是数字 S，另外一个是表达式且其类型标示为 T，那么，若数字 S 在 T 的范围内，则转换为 T 类型；若 S 超出了 T 类型的范围，则 T 转换为 S 类型 。 
4. 若两个操作数都是直接量数字，则返回值类型为范围较大者



例题：以下JAVA程序的运行结果是什么（来自：[牛客网](https://www.nowcoder.com/questionTerminal/701d348fec8f4c1893740e253217a65f)）

```java
public static void main(String[] args) {
    Object o1 = true ? new Integer(1) : new Double(2.0);
    Object o2;
    if (true) {
        o2 = new Integer(1);
    } else {
        o2 = new Double(2.0);
    }
    System.out.print(o1);
    System.out.print(" ");         
    System.out.print(o2);
}
```

* A. `1 1`
* B. `1.0 1.0`
* C. `1 1.0`
* D. `1.0 1`

> 选择 D，三元操作符如果遇到可以转换为数字的类型，会做自动类型提升。



