---
layout: post
title:  "Javascipt Function"
date:   2017-08-31
tags: [JavaScript]
---

根据 Ray Villalobos 的课程总结

#### function 形式

```
function name (parameters){
  statements;
  return;
}
```
**return** 可以返回一个值，或者 object 和 function


#### Declaration

两种方法可以声明一个方程，第一种是正常的方法

```
function plus(a,b){
  var sum = a + b;
  return sum;
}
```
invoke function

`plus(2,2)`


第二种方法：definition expression

```
var plus = function(a,b){
  var sum = a + b;
  return sum;
}

`plus(2,2)`
```
这种方式更加灵活，可以立即调用函数，直接在函数后添加（ )，适合那种只需要调用一次就不在调用的函数

```
var plus = function(a,b){
  var sum = a + b;
  return sum;
}(2,2);
```
#### Invoke

函数写完不会执行，直到我们调用这个函数。

有四种方式调用一个函数
- Function
- Method
- Constructor
- Call & Apply method

前两个是常规经常使用的方式

函数接受 **参数** **this** 和 **arguments**(一个特殊对象)

arguments 返回输入函数的参数
this 代表 object 本身，如果找不到会向上直到找到全局对象 windows

#### Function in Object

```
var calc = {
  status: "A",
  plus: function(a,b){
    ...
  },
}

calc.plus(2,2);
```
在 object 中的 function 使用 this 代表的是这个 object 本身， 所以 this 在 object 中使用非常强大，可以调用 object 中所有的属性和方法

#### invoking instance through the constructor

Function can create the Object - Constrict an Object

这个方法需要使用关键词 new

```
// Constructor
var Dog = function(){
  var name, breed;
  return console.log(this);
}

// first instance
firstDog = new Dog;
firstDog.name = "Rover";
firstDog.breed = "Doberman";

// second instance
secondDog = new Dog;
secondDog.name = "Fluffy";
secondDog.breed = "poodle";
```
1. 注意大写的地方

2. 使用 new 初始化

3. this 表示了 Dog{} 这个 Object 的每一个实例

4. 这种方法适合 object oriented programming

#### Prototype Object

javascript 使用 prototype 继承
