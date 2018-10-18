## JRE和JDK
* JRE (Java Runtime Environment): Java程序设计语言 + Java虚拟机 + Java API类库
* JDK (Java Development Kit): Java API类库中的Java SE (Standard Edition) API子集 + Java虚拟机
## Java虚拟机运行时数据区域
1.程序计数器(线程私有)
  当前线程所执行的字节码的行号指示器
2.Java虚拟机栈(线程私有)
  存储局部变量表、操作数栈、动态链接、方法出口等信息
  局部变量表存放了编译器克制的各种基本数据类型、对象引用和returnAddress类型
3.本地方法栈(线程私有)
  为Native方法服务
4.Java堆(线程共享)
  存放对象实例和数组
5.方法区(线程共享)
  存储已被虚拟机加载的类信息、常量、静态变量、即时编译器编译后的代码等数据
## 垃圾收集(Garbage Collection, GC)
1. 哪些内存需要回收
2. 什么时候回收
3. 如何回收
## Java内存管理
## Java垃圾回收
## Java的四个基本特性(抽象、封装、继承、多态)
## Java和C++的区别
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
