---
title: java虚拟机
comments: true
date: 2023-03-24 16:12:28
updated:
categories:
- [编程语言, java]
tags:
- 编程
---

## JDK介绍

![Lightbox](https://raw.githubusercontent.com/zhengzp2019/Image/main/gfgjdk-660x423.jpg)

- javac
- jar
<!-- more -->
### JVM组成

![jvm](https://raw.githubusercontent.com/zhengzp2019/Image/main/jvm-3.jpg)

### 类装载器(Class Loader Subsystem)

主要由以下三个过程组成

- Loading
- Linking
- Initialization

**Loading：** Class loader读取`.class`文件，生成相应的字节码并存储在Method Area中。对于每一个`.class` ，JVM将如下信息存储在Method Area中.

**Linking:** 平台检验，准备和

**Initalization:**

### JVM 内存(JVM Memory)

1. **方法区(Method area)：**

   存储所有的类层次的信息，比如类名，父类名，方法和变量等信息。在JVM中只有一个方法区。

2. **堆内存(heap aera)：**

   存储一些对象信息，在JVM中只含有一个堆内存，是一个共享资源。

3. **栈内存(JVM language Stack)：**

   ![img](https://pic4.zhimg.com/80/v2-d3dc1ca8eb6a250b3e8f3a4203169233_720w.webp)

   对于每一个线程，JVM都会建立一个这样的栈内存。栈中存放的栈元素叫做活动栈帧( activation record/stack frame)，每个栈帧对应一个被线程调用的方法，在栈帧中包括局部变量表(local variable)，操作数栈(opeand stack)，方法返回地址(return address)和一些额外的附加信息。当一个线程执行结束后，该内存空间被释放，这不是一个共享资源。

4. **程序计数器(Program Counter Register)：**

5. **本地方法区**

![jvm2](https://raw.githubusercontent.com/zhengzp2019/Image/main/jvm-memory-2.jpg)

### 执行引擎(Execution Engine)

### JAVA本地接口(JAVA Native Interface)

## 字节码与机器码的区别

### 字节码

字节码是位于源码和机器码中间层次的编码方式，是由Java编译器从源码编译而来供JVM执行的编码。

字节码无法直接在操作系统上执行，只有由解释器(Interpreter)解释成机器码后才能够在操作系统上执行，而字节码所需要的解释器就位于JVM中。字节码在JVM上执行过程实际上是由JVM将字节码解释成计算机能认识的编码后，供计算机执行，即所谓的机器码。所以只要操作系统由JV

### 机器码

机器码是计算机能够认识的唯一的编码方式，是由一系列的0/1二进制组成的，供CPU执行。机器码经过对Java源码的编译与解释后得到。

### Java语言的编译过程

源码->字节码->机器码

![img](https://raw.githubusercontent.com/zhengzp2019/Image/main/java-platform-independent.png)

### JAVA是如何实现与平台无关的特性的？

正如上面所说Java是通过JVM编译，解释后转化为机器码的，所以只要操作系统提供了JVM，就能够执行Java代码，所以Java的平台无关特性实际上是在操作系统层和Java层加入了一个JVM使Java与平台无关。

但是在不同的操作系统下JVM是不同的，即JVM是平台相关的。对于不同操作系统需要下载不同版本的JVM，而一系列的JVM都在Java的官网中提供。