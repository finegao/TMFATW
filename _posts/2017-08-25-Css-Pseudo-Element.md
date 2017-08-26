---
layout: post
title:  "Pseudo Element"
date:   2017-08-25
tags: [Css selector]
---
#### 伪元素

> A CSS pseudo-element is used to style specified parts of an element.

所以伪元素是修饰元素的某个部分的，比如

- Style the first letter, or line, of an element
- Insert content before, or after, the content of an element

#### Syntax
```
selector::pseudo-element {
    property:value;
}
```
> Notice the double colon notation - ::first-line versus :first-line

> The double colon replaced the single-colon notation for pseudo-elements in CSS3. This was an attempt from W3C to distinguish between pseudo-classes and pseudo-elements.

> The single-colon syntax was used for both pseudo-classes and pseudo-elements in CSS2 and CSS1.

> For backward compatibility, the single-colon syntax is acceptable for CSS2 and CSS1 pseudo-elements.

Css3 为了区分伪类和伪元素，让伪元素使用两个冒号，伪类使用一个冒号。

#### ::first-line

只能使用在 block / inline-block 元素上

#### ::first-letter

只能使用在 block / inline-block 元素上

<mark>多个伪类或者伪元素使用时，要么准确定位，要么想好相互之间的影响，注意后面的会覆盖前面的</mark>

#### ::before / ::after

和前面的改变式样不同，这两个选择器是添加内容。

```
a:after {
    content: " (" attr(href) ")";
}

```

注意 content 属性

#### ::selection

> The ::selection pseudo-element matches the portion of an element that is selected by a user.

很有意思的属性可以对用户鼠标选中的内容设置式样，添加背景，改变 cursor 之类的

不同浏览器对于伪元素的式样支持的不同

#### Generated content

**::before** / **::after**

这两个伪元素和名字一样可以产生内容，其中使用 content 属性添加内容，也可以加入其它 css 属性修饰 content

```
p::before{
  content:"hello";
  css...;
}

p::after{
  content:"hello";
  css...;
}
```
#### CSS content Property

- normal 语义上是默认状态，功能和 none 相同
- none
- counter 又一个很有意思的 css 属性
- attr() html 属性
- string
- open-quote 前引号
- close-quote 后引号
- no-open-quote
- no-close-quote
- url()
