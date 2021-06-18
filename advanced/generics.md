# 泛型

### 基本概念

泛型是泛型编程中一种工具，于 2004 年在 J2SE 5.0 版中添加到 Java 编程语言中。旨在扩展 Java 的类型系统，以允许 “一种类型或方法在提供编译时类型安全的同时对各种类型的对象进行操作” 。

> **Generics** are a facility of generic programming that were added to the Java programming language in 2004 within version J2SE 5.0. They were designed to extend Java's type system to allow "a type or method to operate on objects of various types while providing compile-time type safety". The aspect _compile-time type safety_ was not fully achieved, since it was shown in 2016 that it is not guaranteed in all cases.   \(From: [Generics in Java - Wikipedia](https://en.wikipedia.org/wiki/Generics_in_Java)\)

此外，泛型也被称为参数化类型。



### 为什么需要泛型

首先，我们来看泛型的引入解决了什么问题。在泛型出现之前的代码如下所示：

在向 List 等对象添加值时，可以向其中操作任意类型的值，然后在使用时再转换为其原始类型。在代码出错的清空下，如果将不正确的类型添加到 List 中，直到执行类型转换前都不会产生任何报错。

```java
List list = new ArrayList();
list.add(126L);
list.add("126");                 // 编译不报错，允许添加放入任意对象

Long num1 = (Long) list.get(0);
Long num2 = (Long) list.get(1);  // 编译不报错，运行时报错：ClassCastException
```

而在使用泛型后，List 对象支持指定其成员值类型，此后如果 List 对象接收到非对应类型的对象会产生编译报错，获取其成员值时也不再需要手动转换类型。

```java
List<Long> listB = new ArrayList<>();
listB.add(126L);
listB.add("126");                       // 这里将在编译时报错

Long num3 = listB.get(0);
Long num4 = listB.get(1);               // 获取对象时不需要手动判断和转换和类型
```



由此可见，**泛型可以帮助编译器提供类型安全检测机制，提高了安全性，减少了使用错误类型的对象的错误，同时还提高了代码可读性，快速帮助理解对象所支持的类型**。



### 泛型的用法

泛型有 3 种定义方法：泛型类，泛型方法，泛型接口，例子如下：

```java
// 泛型类
public class GenericsTest<T> {
	T field1;
}

// 泛型方法
public class GenericsUtils {
	public <T> static void testMethod(T t) {
	}
}

// 泛型接口
public interface GenericsInterface<T> {
}
```





