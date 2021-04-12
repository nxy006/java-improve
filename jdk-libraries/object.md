# Object

在  Java 中，Object 类是所有类都具有共同的父类，无论它们是否做了明确声明。因而，理解 Object 类就是理解 Java 对象的通用约定。

## Object 类的方法

* getClass：获取当前对象的类型，是一个 `native` 且 `final` 的方法
* equals：比较两个对象的值是否相等
* hashCode：获取当前对象的哈希值
* toString：返回当前对象的字符串表示
* clone：获取当前对象的克隆对象，即返回新创建、但值相等的实例
* wait / notify / notifyAll：多线程相关方法，用于控制锁的等待和唤醒，均为 `final` 方法
* finalize：被垃圾回收时可能被调用



## 如何设计新的类

Object 提供了五个非 final 方法：`hashCode`、`equals`、`clone`、`toString`、`finalize`，且它们都有自己的含义，任何一个类，在覆盖这些方法时，都应该遵循它们的通用约定。否则，依赖于这些约定的类（比如 HashMap）就可能无法与这些类一起正常运作。



### 如何覆盖 `equals` 方法？

`equals`方法用于表达 “两个对象的值是否相等”，用于判断两个不同实例是否可以视为相等的。比如 HashMap、HashSet 使用此方法判断当前集合中是否存在与某个值相等的实例。

**默认实现**：Object 中 `equals`方法的默认实现是返回对象地址是否相同，此时类的每个实例都只与它自身相等。

```text
public boolean equals(Object obj) {
    return (this == obj);
}
```

{% hint style="danger" %}
**`equals` 与 `==` 的区别**

我们知道，Java 中已有一种很直观的方式，表达两个变量相等，即双等于号 `==`，甚至 Object 类对 `equals` 的默认实现，就是返回 `==`的结果。但这并不意味着两者是相同的。

* `==`是布尔运算符，其含义是比较两侧参数是否相同。当运算对象是两个指向对象的变量时，实质上是在比较两个变量的值 —— 实例地址（堆地址），是否相等。
* `equals` 则不同，它表达的是两个实例的值是否相等，比如两张不同编号的一元钱，尽管是不同的钱（实例），但其所代表的价值（值）是相同的。
{% endhint %}

\*\*\*\*

#### **何时应该覆盖默认实现？**

如果程序满足以下任一条件，则默认实现就是 `equals`  方法所期望的样子，无需覆盖：

* **类的每个实例本质上都是唯一的**：对于表示活动实体，而非值的类而言，其实例本身正是唯一表示。比如： `Thread`。
* **类没有必要提供 “逻辑相等”（logical equality）的测试功能**：例如 `java.util.regex.Pattern` 可以覆盖 `equals` 方法，但设计者不认为用户需要这样的功能，因而没有覆盖。
* **超类已经覆盖了 equals，且超类的行为对当前类也合适**：例如大多数 `Set` 实现都从 `AbstractSet` 继承其  equals 实现，又如 List 实现之于 `AbstractList` 类，Map 实现之于 `AbstractMap` 类。
* **类是私有的，或者是包级私有的，可以确定它的 equals 方法永远不会被调用**：如果非常需要规避风险，还可以覆盖 equals 方法，使之抛出异常，以避免意外的调用。

而如果类具有的自己特有的 “逻辑相等”（logical equality）概念且超类没有实现可用的 equals 方法时，此时就应该覆盖 `equals` 方法。

{% hint style="success" %}
**值类（value class 或 Value-based Classes）**

需要覆盖 `equals` 方法的类，通常属于值类的情形。值类是仅仅表示一个值的类，例如 Integer 或 String，程序在比较这样的实例对象时，希望知道它们逻辑上是否相等，而非是否是同一个实例。

但也有一种值类不需要覆盖`equals` 方法，也就是上述第一条所说明的 “每个值至多只存在一个实对象” 的类，枚举就属于这种情况。对这样的类而言，逻辑相同与对象相同是一回事。
{% endhint %}



#### 覆盖 `equals` 方法的通用约定

equals 方法实现了等价关系（equivalence relation），其属性如下：

* **自反性（reflexive）**：任何非 null 的引用值 `x`，其 `x.equals(x)` 必须返回 `true`，即与自身相等
* **对称性（symmetric）**：对任何非 null 的引用值 `x`，`y`，如果 `x.equals(y)` 返回 `true`，则 `y.equals(x)` 必须也返回 `true`。
* **传递性（transtitive）**：对任何非 null 的引用值 `x`，`y`，z，如果 `x.equals(y)` 返回 `true`，且
  * 果 `y.equals(z)` 返回 `true`，则 `x.equals(z)` 必须也返回 `true`。
* **一致性（consistent）**：对任何非 null 的引用值 `x`，`y`，只要 equals 比较操作中使用的对象信息没有修改，多次调用 `x.equals(y)` 的返回保持一致
* 任何非 null 的引用值 `x`，其 `x.equals(null)` 必须返回 `false`。

{% hint style="success" %}
**违反通用约定时会发生什么？** 

可参考：《Effective Java \(Third Edition\)》第10条：覆盖 equals 时请遵守通用约定
{% endhint %}



### 如何覆盖 `hashCode` 方法？



{% hint style="warning" %}
**待补充**：`hashCode`方法相关

参考：《Effective Java》第11条：覆盖 equals 时总要覆盖 hashCode
{% endhint %}









