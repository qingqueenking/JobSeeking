## JRE和JDK
* JRE (Java Runtime Environment): Java程序设计语言 + Java虚拟机 + Java API类库
* JDK (Java Development Kit): Java API类库中的Java SE (Standard Edition) API子集 + Java虚拟机
## Java虚拟机运行时数据区域
1. 程序计数器 (线程私有) <br>
当前线程所执行的字节码的行号指示器
2. Java虚拟机栈 (线程私有) <br>
存储局部变量表、操作数栈、动态链接、方法出口等信息 <br>
局部变量表存放了编译器克制的各种基本数据类型、对象引用和returnAddress类型
3. 本地方法栈 (线程私有) <br>
为Native方法服务
4. Java堆 (线程共享) <br>
存放对象实例和数组
5. 方法区 (线程共享) <br>
存储已被虚拟机加载的类信息、常量、静态变量、即时编译器编译后的代码等数据
## 垃圾收集(Garbage Collection, GC)
1. 哪些内存需要回收 <br>
Java堆和方法区
原因：程序计数器、虚拟机栈、本地方法栈三个区域随线程而生，随线程而灭；栈中的栈帧随着方法的进入和退出执行入栈和出栈操作，每一个栈帧中分配多少内存基本上在类结构确定下来时就已知，因此这三个区域的内存分配和回收都具备确定性。而Java堆和方法区中的内存分配和回收都是动态的。
2. 什么时候回收
3. 如何回收
4. 回收哪些对象
  * 引用计数算法
  * 可达性分析算法
## Java内存管理
## Java垃圾回收
## Java的四个基本特性(抽象、封装、继承、多态)
## Java和C++的区别
## 内存泄漏和内存溢出
1. 内存泄漏 (Memory Leak)
2. 内存溢出 (Memory Overflow)
3. Out of Memory
## 引用
1. 强引用 (Strong Reference) <br>
强引用是指程序代码中普遍存在的，类似"Object obj = new Object()"这类的引用 <br>
只要强引用还在，垃圾收集器永远不会回收掉被引用对象。
2. 软引用 (Soft Reference) <br>
使用SoftReference类来实现 <br>
当内存空间还足够时，能保留在内存之中；在系统将要发生内存溢出异常之前，将会把这些对象列进回收范围之中进行第二次回收，如果这次回收还没有足够内存，才会抛出内存溢出异常。
3. 弱引用 (Weak Reference) <br>
使用WeakReference类来实现 <br>
当垃圾收集器工作时，无论当前内存是否足够，都会回收掉只被弱引用关联的对象。
4. 虚引用 (Phantom Reference) <br>
使用PhantomReference类来实现 <br>
一个对象是否有虚引用的存在，完全不会对其生存时间构成影响，也无法通过虚引用来取得一个对象实例。为一个对象设置虚引用关联的唯一目的就是能在这个对象被垃圾回收器回收时收到一个系统通知。
## Overload和Override的区别
## 访问修饰符
## 基本数据类型和包装类
## 自动拆装箱
## 抽象类和接口的区别
## 常用的Java包
## String、StringBuilder、StringBuffer
## Object类
## Java的集合类
## HashMap的底层实现
## HashMap、Hashtable、ConcurrentHashMap
## ArrayList、LinkedList
## 异常
## 多线程的实现方式
## 线程状态转换
## 线程安全
## 线程池
## volatile
## Synchronized和Lock的区别
## 死锁
## BIO、NIO、AIO
## 序列化
## 反射
## Java类加载器
## JDBC
## Socket
## The Garbage Collector
An object is eligible for garbage collection when there are no more references to that object.
