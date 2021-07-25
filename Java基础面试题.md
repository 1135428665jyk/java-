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
### （4）简述final作用，为什么局部内部类和匿名内部类只能访问局部final变量？
```bash
final
修饰类，不能继承

修饰方法，不能重写，但是可以重载

修饰变量，表示变量一旦被赋值不能改变他的值

（1）修饰成员变量，如果finalx修饰的是类变量，只能在静态初始化块中指定初始值或者声明该类变量时指定初始值
如果final修饰的是成员变量，可以在非静态初始化块，声明该变量或者构造器中执行初始值。

（2）修饰局部变量，系统不会为局部变量进行初始化，局部变量必须由程序员显示初始化。因为使用final修饰局部变量时，即可以在定义
时指定默认值（后面的代码不能再进行赋值），也可以不指定默认值，在后面的代码块中对final变量赋初值

（3）修饰基本类型和引用数据类型
如果时基本数据类型，则其数值一旦初始化之后便不能更改
如果引用类型的变量，则对其初始化之后便不饿能再让他指向另外一个对象，但是引用的值时可变的。

为什么局部变量和匿名内部类只能访问final变量？
内部类和外部类是同一级别的，内部类不会因为定义在方法中就会随着方法的完毕就销毁，而会复制变量作为内部成员变量，当
外部类销毁，内部类仍然可以访问。将局部变量作为内部类成员变量，必须保证两个变量是一样的。
内部类将局部变量copy一份作为内部类的成员变量

```
### （5）String StringBuilder StringBuffer区别及使用场景
```bash
String 是final不可变的每一次操作都会生成新的对象
StringBuffer和StringBuilder不会改变对象
StringBuffer是线程安全的(Synchronized)，StringBuilder是线程不安全的。
性能：StringBuilder>StringBuffer>String
场景：优先使用StringBuilder，多线程使用共享变量时使用StringBuffer


```
### （6）重载和重写的区别
```bash
重载：发生在同一个类中，方法名称相同，参数类型不同，个数不同，顺序不同，方法返回值和访问修饰符可以不同，发生在编译时。
重写：发生在父子类中，方法名，参数列表必须相同，返回值范围小于等于父类，抛出的异常范围小于等于父类，访问修饰范围大于等于
父类，如果父类父类方法为private则子类不能重写

```
### （7）接口和抽象类区别？
```bash
（1）抽象类可以有实现方法，接口只能是抽象方法
（2）抽象类中的成员变量是各种类型的，而接口中的成员变量只能是public static final类型的
（3）抽象类只能继承一个，接口可以实现多个
（4）接口设计的目的是对类的行为进行约束，提供一种机制，可以强制要求不同的类具有相同的行为，只约束行为的有无，不对实现进行要求
抽象类设计的目的：代码复用，当不同的类具有相同的行为，且其中一部分实现一致时，可以派生出一个抽象类，抽象类时对类的本质
的抽象，表达的是 is a关系，接口是对行为的抽象表达的是 like a的关系。
（5）使用场景，当关注事物的本质用抽象类，当关注行为时，用接口
（6）设计难度，定义抽象类的代价比较高，定义接口在设计阶段会降低难度。
接口中静态方法必须进行实现，接口中定义变量为常量
接口中可以定义default方法，实现类会继承interface中default方法，如果一个类实现A,B这两个类都有相同default方法
那么需要在类中实现此方法
```
### （8）List和Set的区别
```bash
List：有序，按对象进入的顺序保存对象，可重复，允许多个null值，使用iterator取出元素，再逐一遍历，可以使用
get获取下标的元素
Set：无序，不可重复，最多允许一个NULL元素对象，取元素时只能用Iterator接口取得所有元素，再逐一遍历各个元素
```
### （9）HashCode和equals？
```bash
hashCode作用获取哈希码，作用时获取该对象再散列表中的位置。散列表存储的key-Value键值对，
HashSet举例，先判断HashCode判断对象的加入位置，看该位置是否有值，如果没有，hashSet中没有该对象
如果存在，然后调用equals方法，检查两个对象是否真的相同，如果相同不会让其加入成功，否则会加入其中，减少了equals的次数，
大大提高了执行速度。
如果两个对象相同则hashCode一定相同
如果两个对象相同，调用equals则相同
如果两个对象有相同的hashCode，他们不一定相等
如果没有重写hashCode则该class的两个对象无论如何都不会相等。

```
### （10） ArrayList和LinkedList区别
```bash
ArrayList:基于动态数组，连续内存空间，适合随机访问，当长度超过限制，会自动进行扩容，会重建数组，然后将老数组中的数据copy到新数组中
如果不是尾部插入元素会涉及到大量元素的移动，使用尾插法并且指定容器容量能够提升性能，默认容量是10，会以1.5倍扩容

LinkedList:基于链表结构，内存空间不连续，适合插入及删除元素，不适合查询，LinkedList必须使用Iterator进行遍历，因为使用for循环
还会再重新进行遍历，消耗一定的性能，不要使用indexOf进行遍历，如果找不到元素，会对遍历整个列表。链表结构，不需要设置默认容量，

```
### (11) HashMap和HashTable区别
```bash
HashMap没有synchronized修饰，是线程不安全的，而HashTable是线程安全的
HashMap可以存储Null值而HashTable不能存储Null值
底层实现：
Java8，链表长度达到8，数组长度超过64会转换成红黑树，元素以内部节点Node元素存在
计算key值，二次hash取模，得到对应数组下标，没有hash冲突，则直接创建node节点存入数组
如果产生hash冲突，先进性equal比较，相同则取代该元素，不同则判断链表高度插入链表，链表长度达到8，并且数组长度达到64则转换成
红黑树，长度低于6，则转换成链表。
key为null,存储在下标为0的位置
```
### (12)ConcurrentHashMap 1.7和1.8有什么区别？
```java






```
### (13) HashSet实现原理
```java
HashSet的实现主要是使用HashMap来实现的。
HashSet是使用HashMap的key的不可重复性，来实现的，但是value，

private static final Object PRESENT = new Object(); //value创建的对象
//序列化的时候，不将整个map进行序列化，子序列化key
private transient HashMap<E,Object> map;

其内部存在方法有：

add()
remove()
size()
isEmpty()
contains()
clear()
writeObject()

//写入流对象
private void writeObject(java.io.ObjectOutputStream s)
        throws java.io.IOException {
        // Write out any hidden serialization magic
        s.defaultWriteObject();

        // Write out HashMap capacity and load factor
        //容量
        s.writeInt(map.capacity());
        //加载因子
        s.writeFloat(map.loadFactor());

        // Write out size
        //存储元素的数量
        s.writeInt(map.size());

        // Write out all elements in the proper order.
        //将key，写入到流
        for (E e : map.keySet())
            s.writeObject(e);
    }


//读取流对象
private void readObject(java.io.ObjectInputStream s)
        throws java.io.IOException, ClassNotFoundException {
        // Read in any hidden serialization magic
        s.defaultReadObject();

        // Read capacity and verify non-negative.
        //读取容量
        int capacity = s.readInt();
        if (capacity < 0) {
            throw new InvalidObjectException("Illegal capacity: " +
                                             capacity);
        }

        // Read load factor and verify positive and non NaN.
        //读取加载因子
        float loadFactor = s.readFloat();
        if (loadFactor <= 0 || Float.isNaN(loadFactor)) {
            throw new InvalidObjectException("Illegal load factor: " +
                                             loadFactor);
        }

        // Read size and verify non-negative.
        //读取存储元素的数量
        int size = s.readInt();
        if (size < 0) {
            throw new InvalidObjectException("Illegal size: " +
                                             size);
        }
        // Set the capacity according to the size and load factor ensuring that
        // the HashMap is at least 25% full but clamping to maximum capacity.
        capacity = (int) Math.min(size * Math.min(1 / loadFactor, 4.0f),
                HashMap.MAXIMUM_CAPACITY);

        // Constructing the backing map will lazily create an array when the first element is
        // added, so check it before construction. Call HashMap.tableSizeFor to compute the
        // actual allocation size. Check Map.Entry[].class since it's the nearest public type to
        // what is actually created.

        SharedSecrets.getJavaOISAccess()
                     .checkArray(s, Map.Entry[].class, HashMap.tableSizeFor(capacity));

        // Create backing HashMap
        //因为LinkedHashSet继承于HashSet，兼容了LinedHashSet序列化操作，
        map = (((HashSet<?>)this) instanceof LinkedHashSet ?
               new LinkedHashMap<E,Object>(capacity, loadFactor) :
               new HashMap<E,Object>(capacity, loadFactor));

        // Read in all elements in the proper order.
        //取出元素放到HashMap中或陪着LinkedHashMap中
        for (int i=0; i<size; i++) {
            @SuppressWarnings("unchecked")
                E e = (E) s.readObject();
            map.put(e, PRESENT); //PRESENT是new Object()对象，没有实际含义
        }
    }
    
LinkedHashSet继承HashSet，可以看出其构造函数，都是调用HashSet的构造函数,其余没有特殊的其他方法
    HashSet(int initialCapacity, float loadFactor, boolean dummy) {
        map = new LinkedHashMap<>(initialCapacity, loadFactor);
    }

```




