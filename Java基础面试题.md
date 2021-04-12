## Java基础面试题

### （1）什么是面向对象？谈谈对面向对象的理解
```bash
答：首先需要知道面向过程编程，面向过程是指每一步按照顺序执行，而面向对象会把事务抽象成对象的概念，然后给对象赋值一些属性和方法。

面向过程更高效，面向对象更容易扩展，复用，维护。

面向对象的三大特性：封装，继承，多态。

封装：隐藏对象的属性或方法，仅提供公共访问方式。

继承：提高代码复用性，做出自己的改变或扩展。继承是多态的前提

多态：基于对象所属类的不同，外部对同一方法调用，实际执行的逻辑不同，继承，方法重写，父类引用指向子类对象。（弊端：无法调用子类的特有方法）

面向对象的五大基本原则：

（1）单一职责SRP(Single Responsibility Principle)

类的功能要单一，不能包罗万象

（2）开放封闭原则OCP(Open-Close Principle)

对于扩展开发，对于修改是封闭的

（3）里氏替换原则LSP()

子类可以替换父类出现在父类能够出现的任何地方

（4）依赖倒置原则DIP(the Dependency Inversion Principle DIP)

高层的模块不应该依赖底层模块，他们都应该依赖抽象。抽象不应该依赖具体实现，具体实现应该依赖于抽象

（5）接口分离原则ISP(the Interface Segregation Principle ISP)

设计时采用多个与特定客户类有关的接口比采用一个通用的接口要好。
```


### （2）JDK，JRE，JVM直接的区别与联系
```bash
JDK:Java Development kit java开发工具

JRE:Java Runtime Environment：java运行环境

JVM:Java Virtual Machine java虚拟机

JVM:功能将编译好的class文件进行解释执行，因为class文件不能由操作系统直接执行，需要有jvm解释方可执行。

JRE:由JVM+lib组成，class文件在运行时需要调用各样的java类库，即jvm想要运行class文件必须依赖jre的lib库

JDK:主要面向开发者，具有编译功能，jre主要面向用户，主要是class文件的执行，假如我们只有编译好的class文件和jre，那么就可以运行class了。
```
![image-20210412221102400](C:\Users\JYK\AppData\Roaming\Typora\typora-user-images\image-20210412221102400.png)

### （3）== 和 equals
```bash
== 基本数据类型是变量值，引用类型是队中内存的地址
equals：Object默认采用==比较，通常会重写
String重写equals方法，对比每一个字符。




```


