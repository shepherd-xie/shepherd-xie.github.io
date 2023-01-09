---
title: Java8内存模型
date: 2018-10-25 14:31:00
tags: 
categories: JVM
top:
---

Java8内存模型

![Java8内存模型](https://images.orkva.com/images/2023/01/09/java_runtime_data_areas.jpg)

<!-- more -->

![区域的内存大小](https://images.orkva.com/images/2023/01/09/Cookbook_JVMArguments_2_MemoryModel.png)

| 控制参数 | 使用说明 |
| :---: | :---: |
| -Xms | 设置堆的最小空间大小 |
| -Xmx | 设置堆的最大空间大小 |
| -XX:NewSize | 设置新生代最小空间大小 |
| -XX:MaxNewSize | 设置新生代最大空间大小 |
| -XX:PermSize | 设置永久代最小空间大小 |
| -XX:MaxPermSize | 设置永久代最大空间大小 |
| -Xss | 设置每个线程的堆栈大小 |

1. HEAP：
堆内存由JVM在程序启动时创建，用于存储对象。堆内存可以被任何线程访问，进一步分为三代`Young Generation`，`Old`＆`PermGen`（永久生成）。当对象被创建时，它首先进入Young代（尤其是Eden空间），当对象变老时，它会移动到Old / tenured Generation。在PermGen空间中，存储所有静态和实例变量名称 - 值对（对象的名称引用）。
2. Stack：
使用程序创建的每个线程生成堆栈。它由线程关联。每个线程都有自己的堆栈。所有局部变量和函数调用都存储在堆栈中。它的生命取决于线程的生命，因为线程将存在，它也将存在，反之亦然。它也可以手动增加
3. PC寄存器：
它也与其线程相关联。它基本上是正在执行的当前指令的地址。由于每个线程将要执行的一些方法集取决于PC寄存器。它对每个指令都有一些值，对于本机方法是未定义的。通常用于跟踪指令。
4. Method Area：
它是像Heap这样的所有线程共享的内存。它是在Java Virtual Machine启动时创建的。它包含代码实际上是编译的代码，方法及其数据和字段。运行时常量池也是方法区域的一部分。它的内存默认由JVM分配，如果需要可以增加。运行时常量池是常量表的每个类表示。它包含在编译时定义的所有文字和将在运行时解决的引用。
5. Native方法堆栈本：
机方法是用java以外的语言编写的方法。JVM实现无法加载本机方法，也无法依赖传统堆栈。它还与每个线程相关联。简而言之，它与堆栈相同，但它用于本机方法。
