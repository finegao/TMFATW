---
layout: post
title:  "Object Oriented Design"
date:   2017-08-01
tags: [programming]
---

### 面向对象编程

面向对象编程是用 **抽象** 方式创建基于现实世界模型的一种编程模式。
它使用先前建立的范例，包括模块化，多态和封装几种技术。

相对于 “一个程序只是一些函数的集合，或简单的计算机指令列表。”的传统软件设计观念而言，面向对象编程可以看作是 **使用一系列对象相互协作**
的软件设计。 在 OOP 中，每个对象能够 **接收消息，处理数据和发送消息** 给其他对象。每个对象都可以被看作是一个拥有
**清晰角色或责任的独立小机器**。

面向对象程序设计的目的是在编程中促进更好的灵活性和可维护性，在大型软件工程中广为流行。凭借其对模块化的重视，面向对象的代码开发更简单，更容易理解，相比非模块化编程方法 1, 它能更直接地分析, 编码和理解复杂的情况和过程。


## 术语

![术语](/images/Object Oriented Design MDN 1.png)

更多关于面向对象编程的描述，请参照维基百科的 [面向对象编程][2] 。

## 命名空间

## 标准内置对象

[1]: https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript
[2]: https://zh.wikipedia.org/wiki/%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1


### Object Oriented Design

understand our problem
plan our solution
build the application

analysis
design
programming

waterfall approach
agile/iterative approach

procedural language
logic programming language
functional programming language


OOD thinking represent the thing like the real world

objects
how to describe the object in programming language
indentity+attributes+behavior

Self-Contained：Constituting a complete and independent unit in and of itself

Object are not always physical/visible items

Noun = Object

### Class

OOD is not about objects, it is about Class, because we use classes to create objects

class describe what an object will be, but it isn't the object itself
A class is blueprint, a detailed description, a definition.

Class

name/type/identity

property/data

operation/method/behavior

所以考虑Class时，一定要考虑三个方面，它的名字，它的属性，或者数据和变量，最后是行为或者方法和方程

create the object base on the class/ create the instance of the object

each object is an instance of a particular class

the process of creating these objects is called **instantiation**

![object and class](/images/class1.png)

所以写 object 前， 一定要有一个 class.

大多数语言内置很多class，这些不需要我们去写.

### A PIE

四种建立 Class 的基本思想
Abstraction/Polymorphism/Inheritance/Encapsulation

**Abstraction**
focus on the essentials
ignore the irrelevant
ignore the unimportant

抽象就是提取一类事物的重要的本质特征，而忽略其不重要的。
抽象是建立类的基础，比如如何建立一个 table 的类，我们要提取哪些特征

**Encapsulation**
封装

封装实质上是通过将相关的一堆函数和一堆对象放在一起，对外有函数作为操作通道，对内则以变量作为操作原料。只留给外部程序员操作方式，而不暴露具体执行细节。大部分书举的典型例子就是汽车和灯泡的例子：你不需要知道不同车子的发动机原理，只要踩油门就可以跑；你不需要知道你的灯泡是那种灯泡，打开开关就会亮。

**Inheritance**
继承

reuse code base on the existing class

比如 class Person / class Customer

Customer 继承 Person 所有的属性和方法，然后再添加自己的属性和方法就好了

superclass / subclass
parent class / child class

**Polymorphism**

Polymorphism means *many forms*

多态的理解，多态就是有一个父类然后有多个不同的子类，子类继承了父类的方法，但是有的子类继承的这个方法会有不同行为。
还是同样的方法，但是会有一些改动，这时候需要重写这个方法覆盖父类的方法

比如 父类 银行账户 有一个取款的方法 子类中 活期账户，定期账户，投资账户 都要有取款的方法，但是他们取款的方法各有不同，比如活期会有一笔手续费，
定期要提前三十天，所以虽然他们继承了父类的方法，但是要重写这个方法覆盖父类的方法。这样每个子类对于取款都有自己的实现，这就实现了多态。

所以要有父类和多个子类，也就是继承
要有方法的重写

[多态菜鸟教程][1]


### Object oriented analysis and design

所以该如何创建类 创建怎么样的类 这里指的是思考过程 不是实现机制

1 gather requirements
2 describe the application
3 identify the main objects
4 describe the interactions between the objects
5 create a class diagram

### UML

Unified Modeling Language

# UML Tool
[gliffy][https://www.gliffy.com/]
[cretaly][https://creately.com/]
[lucidchart][https://www.lucidchart.com/]

### Use Case

Use Cases
1 title: what is the goal
2 actor: who desires it
3 scenario: how is it accomplished

通过 Use cases 我们可以理解需求，并且以此建立我们的类

### Domain Modeling

# identify the classes and the relationship between classes

面向对象的思想是接近现实世界的构建，所以 use case 中的 scenario 描述，是对现实世界的一种描述
那么，从那些描述中我们可以提取构建这个世界的元素，对象以及对象之间的关系，名词是对象，动词

# class diagram

![class diagram](/images/class2.png)
加号表示public，减号表示private。 尽量多写private，只有当确定某个方法要和其他的对象交换数据时，才是public。

然后按照 class diagram 转化为代码

# Constructor

是一类特殊的方法，在用new创建object时会调用class的构造函数。
![Constructor](/images/class3.png)

# static attributes and methods
静态属性或者方法可以被其他类引用，相当于一个全局变量。

# 多态的再次理解

再次理解多态，首先我们都是先写继承，然后子类添加父类中没有的方法，有时候我们还要改写从父类继承的方法，这些子类呈现的就是多态

# abstract class

这个class 就是为了创建其他的 object 用的，所以并不会初始化它，它携带了子类需要用到一般性属性和方法，只是为了方便创建子类。

# interface
接口

各种类可以不用多个继承（java只能单继承），直接利用接口实现功能。

# aggregation/composition

包含关系
继承是 IS A ： the dog is an animal

包含是 HAS A ：the car has an engine

aggregation： a classroom has many students
composition： a document has many pages

两者的区别是删除容器会不会影响其包含的内容

# design pattern

# principle
SOLID/GRASP





[1]: http://www.runoob.com/java/java-polymorphism.html
