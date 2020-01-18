# 与其他语言的对比

## 析构函数

析构函数是 C++ 的概念，用于垃圾清理时调用它会在每次删除所创建的对象时执行。其名称与类名完全相同，只在类名加了波浪号（~）作为前缀，无返回值，也不带有任何参数。

java 提供 finalize\(\) 方法，垃圾回收器准备释放内存的时候，会先调用 finalize\(\) 方法。但与 C++ 不同的是，Java 的内存回收是不确定的，在仍有剩余空间时很可能不会立即释放空间。这也就意味着，我们无法知道它何时被调用。

finalize\(\) 的一般用法是清理本地内存（不由 JVM 管理的外部内容，如本地方法创建出的内容），不应该在其中包含任何业务代码。

参考：《Java 编程思想》 5.5.1 finzlize\(\) 方法的用途何在



## 虚函数（纯虚函数）

> C++、Object Pascal 等语言中有虚函数（英语：virtual function）或虚方法（英语：virtual method）的概念。这种函数或方法可以被子类继承和覆盖，通常使用动态调度实现。这一概念是面向对象程序设计中（运行时）多态的重要组成部分。简言之，虚函数可以给出目标函数的定义，但该目标的具体指向在编译期可能无法确定。
>
> 来自：[维基百科](https://zh.wikipedia.org/wiki/%E8%99%9A%E5%87%BD%E6%95%B0)

以下是 C++ 中虚函数的例子（普通成员函数加上virtual关键字就成为虚函数）：

```cpp
# include <iostream>
# include <vector>

using namespace std;
class Animal
{
public:
    virtual void eat() const { cout << "I eat like a generic Animal." << endl; }
    virtual ~Animal() {}
};

class Wolf : public Animal
{
public:
    void eat() const { cout << "I eat like a wolf!" << endl; }
};
```

**在 Java 中, 动态绑定是 Java 的默认行为。所有的方法默认都是"虚函数"，只有以关键字 final 标记的方法才是非虚函数。**

> 纯虚函数或纯虚方法是一个需要被非抽象的派生类覆盖（override）的虚函数. 包含纯虚方法的类被称作抽象类; 抽象类不能被直接实例化。 一个抽象基类的一个子类只有在所有的纯虚函数在该类\(或其父类\)内给出实现时, 才能直接实例化. 纯虚方法通常只有声明\(签名\)而没有定义\(实现\)，但有特例情形要求纯虚函数必须给出函数体定义.

纯虚函数的定义仅提供方法的原型. 虽然在抽象类中通常不提供纯虚函数的实现, 但是抽象类中可以包含其实现。

在C++语言中, 纯虚函数用一种特别的语法`[=0]`定义（但 VS 也支持 abstract 关键字）, 示例如下：

```cpp
class Abstract {
public:
   virtual void pure_virtual() = 0;
};
```

**在 Java 中，纯虚函数相当于抽象函数。**

