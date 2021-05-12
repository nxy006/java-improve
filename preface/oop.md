---
description: 面向对象编程（Object-oriented Programming，OOP）的基本概念
---

# 面向对象语言

## 编程范型 <a id="firstHeading"></a>

**编程范型**（Programming paradigm）是指软件工程中的一类典型的编程风格，目前主流编程范型包括：

* 面向过程编程（Procedural programming）
* 面向对象编程（Object-oriented programming，OOP）
* 函数式编程（functional programming）

编程范型提供并决定了程序员对程序执行的看法，面向对象编程将 “对象” 作为程序的基本单元，将程序和数据封装其中，程序会被设计成彼此相关的对象。

同理，面向过程主要要采取过程调用或函数调用的方式来进行流程控制；函数式编程则将电脑运算视为函数运算，并且避免使用程序状态以及易变对象。



**面向对象编程语言**（Object-oriented Programming Language，OOPL）是支持面向对象编程范型的编程语言。广义而言，包括任何支持 “对象" 概念的编程语言；严格意义角度，则只包括那些具有足够多面向对象特征的语言。

{% hint style="success" %}
面向对象编程语言目前并没有确切的定义，我们并没有一个公允的标准用于判断。甚至随着理论的演化，某些特性也不再认为是必须的（比如：继承），下面的例子展示了某些反例：

* JavaScript，不支持封装和继承特性，但一般认为它是面向对象的语言
* golang，不支持继承特性，但一般认为它是面向对象的语言
{% endhint %}



## 面向对象的三大特征？

封装、继承、多态

{% hint style="success" %}
**面向对象的四大特性：**封装、抽象、继承、多态。

相比三大特征，这里增加了抽象。抽象指的是如何隐藏方法的具体实现，让调用者只需要关心方法所提供的功能，而无需关注具体实现。合理使用抽象，能够帮助使用者过滤非必要的信息。

抽象作为一种通用的设计思想，不仅限于面向对象编程中使用，也无需编程语言提供某种特殊的支持，因而往往不被认为是面向对象的特征之一。
{% endhint %}









## 参考文档

1. [设计模式之美 - 极客时间](https://time.geekbang.org/column/intro/250)（收费课程）
2. [Object-oriented programming - Wikipedia](https://en.wikipedia.org/wiki/Object-oriented_programming)
3. \*\*\*\*



