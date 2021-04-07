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

{% hint style="danger" %}
**`equals` 与 `==` 的区别**

我们知道，Java 中已有一种很直观的方式，表达两个变量相等，即双等于号 `==`，甚至 Object 类对 `equals` 的默认实现，就是返回 `==`的结果。但这并不意味着两者是相同的。

* `==`是布尔运算符，其含义是比较两侧参数是否相同。当运算对象是两个指向对象的变量时，实质上是在比较两个变量的值 —— 实例地址（堆地址），是否相等。
* `equals` 则不同，它表达的是两个实例的值是否相等，比如两张不同编号的一元钱，尽管是不同的钱（实例），但其所代表的价值（）是相同的。
{% endhint %}



**默认实现**：Object 中 `equals`方法的默认实现是返回对象地址是否相同，此时类的每个实例都只与它自身相等。

```text
public boolean equals(Object obj) {
    return (this == obj);
}
```



{% hint style="warning" %}
**待补充**：equals 方法的通用约定 etc. 

参考：《Effective Java》第10条：覆盖 equals 时请遵守通用约定
{% endhint %}



### 如何覆盖 `hashCode` 方法？



{% hint style="warning" %}
**待补充**：`hashCode`方法相关

参考：《Effective Java》第11条：覆盖 equals 时总要覆盖 hashCode
{% endhint %}









