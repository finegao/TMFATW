---
layout: post
title:  "Writing Efficient Selector"
date:   2017-08-26
tags: [Css selector]
---

#### Css 选择器写法总结

1. Make selector as simple as possible
  - 复杂的选择器解析的时间会很长，所以越简单越短越好。
2. The "key" selector should be as specific as possible
  - key selector 指的是最右端的选择器，由右端的选择器控制定位，左端负责式样
3. Take advantage of inheritance
  - 要分析页面的结构，相同的构造式样由父元素界定，只写局部式样
4. Limit complex selector
  - 减少全局选择器，伪类和伪元素的使用，如果其他选择器可以做到就不要用之前提到的选择器，他们的解析时间更长
5. Remove ununsed selector
  - 使用框架比如 bootstrap 时，把不需要的式样删除

#### Properly structure HTML

1. Focus on clean, semantic code  
  符合语义，比如作者等信息，使用 blockquote 而不是 p ， 那么引用的信息更好控制。修改时不用单独选取引用的 p 元素，而且所有的 引用元素 又可以统一控制。

2. Structure code consistently
  Html 代码类似的内容使用相同的标签和结构

3. Keep Html code as simple as paossbile
  专注于页面结构和内容，不要为了视觉效果加了很多 div，往往这样适得其反，因为更简单的结构更有利于 css 选择器找到元素施加式样。

#### Strategies for Writing selector

根据网站规模的不同有不同的策略

1. 小型网站

使用元素选择器可以很好关联html结构，比如一个 main 元素里有 div 元素，div 元素中有 p 和 a 元素
```
main div
main div p
main div a
```
2. 大型网站

大型网站有更复杂的机构，使用上面的方法往往 css 往往更加复杂，使用 class 是更好地选择

```
.modal
.modal p
.modal a
```
#### style sheet seperation

选择使用一个唯一的 css 文件，还是使用多个分类的 css 文件，比如字体，布局等

#### Reuse css

可以借用之前项目的 css， 那么在编写 css 时就要养成模块化的习惯，良好的命名可以使 css 重复使用。

#### Some Css

- [Object Oriented CSS](https://github.com/stubbornella/oocss/wiki)
- [SMACSS](https://smacss.com/) 不是一个框架，而是一个写作指导
- [Pattern Lab](http://patternlab.io/)
- [4 level css selector](https://www.w3.org/TR/selectors4/)

#### Css resource

- W3C CSS
- MDN CSS
- Css-Tricks
