---
layout: post
title:  "算法"
date:   2017-08-23
tags: [算法]
---
### Algorithm

DSA: Data Structure + Algorithm

#### 有穷性

算法必须有穷的，否则是个死循环。

例子：hailstone sequence 冰雹序列

#### 健壮

健壮指的是程序不知能够正确的输入，而且还能对错误的输入进行反馈

#### 效率

最重要的是效率

#### 性能测度

性能测度是测量效率的

> To measure is to know,
> If you can not measure it,
> you can not improve it
> \- Lord Kelvin

测度： 时间成本 + 空间成本

#### 图灵机

[图灵机 wiki](https://zh.wikipedia.org/wiki/%E5%9B%BE%E7%81%B5%E6%9C%BA)

图灵机模拟自然计算的过程

#### RAM

RAM：Random Access Machine

图灵机和RAM模型都是性能测度工具测度

#### 大O记号

这是一种测度性能的渐进分析，就是在问题规模足够大时，计算成本如何增长。所以我们主要是看它的变化趋势，也就是斜率，随着 n 的增加，时间的变化剧烈程度。

T(n) = O(f(n))

常系数可忽略：O(f(n)) = O(c * f(n))  
低次项可忽略：O(n^a + n^b) = O(n^a) a > b

有些算法在 n 小的时候时间成本反而比 n 大的时候要高

#### 高效解

常数方程 O(1)，如果有算法可以达到 O(1)，那么它是最高效的。

对于没有 循环/分支/递归 的算法可以认为是 O(1) 复杂度。

对数方程 O(log n) 底数可以忽略，这类也是高效的，因为会接近常数方程

#### 有效解

多项式复杂度 O(n^k)，可以忽略低次项，最高次项的常数也可以忽略

线性复杂度 O(n)

#### 难解

指数复杂度 O(2^n) 往往认为是不可取的，但是算法的指数复杂度解往往比较容易得到，而多项式反而不容易得到。
