# 基本运算

### 取模运算（mod）

取模运算，结果的符号和被除数符号一致

```java
int x = -5;
int y = -12;
System.out.println(y % x);  // -2
```

### 优先级问题

Q1-表达式\(short\)10/10.2\*2运算后结果是什么类型？（来自：[牛客网](https://www.nowcoder.com/questionTerminal/d769be9a6dae4c3088403c5de56427ef)）

> double，强制类型转换的优先级高于+ - \* /

### 运算中的类型转换

运算时，低等级会向高等级转换。

提醒：这种转换是逐个计算中不断转换的。

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

> 经过强制类型转换以后，`short a = 128; byte b = (byte) a;` 变量a, b的值分别为（ ）

* A. 128  127
* B. 128  -128
* C. 128  128
* D. 编译错误

> int占4个字节，32位，byte占1个字节，8位，所以强转时会截断。值为 11111101，因为开头是1，所以为负数。即1个负数的补码是10000000。反码是01111111，原码是1000000。是128.因为是负数，所以是-128。

#### 练习

Q1-如果 `int x=20, y=5`，则语句 `System.out.println(x+y +""+(x+y)+y);` 的输出结果是（）（来自：[牛客网](https://www.nowcoder.com/questionTerminal/152d624072fd4ac4aa5fa4032cb05cd9)）

> 答案是：25255 1. 不论有什么运算，小括号的优先级都是最高的，先计算小括号中的运算，得到x+y +""+25+y 2. 任何字符与字符串相加都是字符串，但是是有顺序的，字符串前面的按原来的格式相加，字符串后面的都按字符串相加，得到25+“”+25+5 3. 上面的结果按字符串相加得到25255

?&gt; Q2-假定x和y为double型，则表达式x=2，y=x+3/2的值是（）（来自：[牛客网](https://www.nowcoder.com/questionTerminal/d38b07cce7c84590a5cf1d8865c1dd13)）

* 3.500000
* 3
* 2.00000
* 3.00000

> 答案是 D

