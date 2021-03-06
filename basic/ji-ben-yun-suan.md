# 基本运算

## 算术操作符

### 取模运算（mod）

取模运算，结果的符号和被除数符号一致

```java
int x = -5;
int y = -12;
System.out.println(y % x);  // -2
```

## 关系操作符

关系操作符返回布尔值，包括小于（`<`），大于（`>`），小于或等于（`<=`），大于或等于（`>=`），等于（`==`）及不等于（`!=`）

## 逻辑操作符

逻辑操作符，由与（`&&`）或（`||`）非（`!`）构成，返回一个布尔值。



### 短路求值（Short-circuit evaluation）

逻辑表达式的短路求值在编程语言中普遍存在，指的是运算表达式时如果发现整个表达式的结果已经可以运算得到，就不再继续运算的特点。

{% hint style="info" %}
在编程中要注意短路求值问题，需要执行的代码不要放入逻辑表达式，即便能够保证它按期望执行也不应该这么做，其他人的轻微改动就可能破坏其正常功能，除非表达式真的非常非常易懂。
{% endhint %}

{% hint style="success" %}
对有些语言而言，除了短路求值，它还提供了非短路求值的方式，比如 Java、C\#、Ruby 都可以使用逻辑运算符替代逻辑运算符，此时将对每个子表达式均求值。常见的逻辑运算符一般包括：&（与）、`|`（或）、`!`/`~`（非）、`^`（异或）。（注：Java 使用`~`表达非。）

对另一些语言，则只提供了短路求值的写法，如果需要非短路求值，只能采用变通的写法，先求出每个子表达式的值，再将其这些用于逻辑判断。比如 C/C++。
{% endhint %}

例题：[牛客网](https://www.nowcoder.com/questionTerminal/8cf208348b5b42a6b509b164efec3cc7)



## 位操作符

位运算符包括：与（`&`），或（`|`），异或（`^`），非（`~`），左移（`<<`），右移（`>>`）。

## 三元操作符

三元操作符指可以对三个参数执行操作的运算符，在 Java 只有一种三元运算符，即： `? :`



### 三元操作符的类型转换

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



## 操作符优先级

Q1-表达式\(short\)10/10.2\*2运算后结果是什么类型？（来自：[牛客网](https://www.nowcoder.com/questionTerminal/d769be9a6dae4c3088403c5de56427ef)）

> double，强制类型转换的优先级高于+ - \* /

## 类型转换操作符



### 运算中的类型转换

运算时，低等级会向高等级转换。（注意：这种转换是逐个计算中不断转换的）

byte 类型的变量在做运算时被会转换为 int 类型的值

* [牛客网](https://www.nowcoder.com/questionTerminal/72bdefc94545490eaad894ad89817580)

 !&gt; 经过强制类型转换以后，`short a = 128; byte b = (byte) a;` 变量a, b的值分别为（ ）

{% hint style="info" %}
经过强制类型转换以后，`short a = 128; byte b = (byte) a;` 变量a, b的值分别为（ ）

* A. 128  127
* B. 128  -128
* C. 128  128
* D. 编译错误
{% endhint %}

> int占4个字节，32位，byte占1个字节，8位，所以强转时会截断。值为 11111101，因为开头是1，所以为负数。即1个负数的补码是10000000。反码是01111111，原码是1000000。是128.因为是负数，所以是-128。

#### 练习

Q1-如果 `int x=20, y=5`，则语句 `System.out.println(x+y +""+(x+y)+y);` 的输出结果是（）（来自：[牛客网](https://www.nowcoder.com/questionTerminal/152d624072fd4ac4aa5fa4032cb05cd9)）

> 答案是：25255
>
> * 小括号的优先级是最高的，先计算小括号中的运算，得到x+y +""+25+y
> * 任何字符与字符串相加都是字符串，但是是有顺序的，字符串前面的按原来的格式相加，字符串后面的都按字符串相加，得到25+“”+25+5
> * 上面的结果按字符串相加得到25255

?&gt; Q2-假定x和y为double型，则表达式x=2，y=x+3/2的值是（）（来自：[牛客网](https://www.nowcoder.com/questionTerminal/d38b07cce7c84590a5cf1d8865c1dd13)）

* 3.500000
* 3
* 2.00000
* 3.00000

> 答案是 D



浮点运算

Java 中，使用 float 和 double 表示浮点数，注意它们不能用于高精度运算，高精度运算需要使用 Big

{% hint style="success" %}
参考：0.1 + 0.2 != 0.3，想知道各个语言的浮点运算的逻辑的可以查看：[https://0.30000000000000004.com/](https://0.30000000000000004.com/)
{% endhint %}

