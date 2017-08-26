---
layout: post
title:  "Css Pseudo Class Selector"
date:   2017-08-24
tags: [Css selector]
---
#### Pseudo-class selector

[伪类](https://www.w3schools.com/css/css_pseudo_classes.asp)是定义元素特殊状态的  
<mark>A pseudo-class is used to define a special state of an element.</mark>

- Style an element when a user mouses over it
- Style visited and unvisited links differently
- Style an element when it gets focus

```
selector:pseudo-class {
    property:value;
}
```

#### Anchor Pseudo-classes

```
/* unvisited link */
a:link {
    color: #FF0000;
}

/* visited link */
a:visited {
    color: #00FF00;
}

/* mouse over link */
a:hover {
    color: #FF00FF;
}

/* selected link */
a:active {
    color: #0000FF;
}
```
1. 默认链接式样带有下划线，使用`text-decoration：none`可以去除。

2 active 比较特殊点击时需要比较强烈的交互，颜色改变或者位置移动,比如

a:active {
    color: #0000FF;
    position: relative;
    top: 1px;
}

链接的四个伪类分别对应

- link 默认式样没有点击之前
- visited 点击之后和 link 相对，表示这个链接之前点击过
- hover 悬停式样
- active 点击的时候，就在点击一瞬间或者按住不放时的式样

注意事项，四个伪类的书写顺序是有要求的,否则伪类无效
- <mark>hover 必须在 link/vistied 之后</mark>
- <mark>active 必须在 hover 之后</mark>

简单的记忆方法 **love+hate**

> Note: a:hover MUST come after a:link and a:visited in the CSS definition in order to be effective! a:active MUST come after a:hover in the CSS definition in order to be effective! Pseudo-class names are not case-sensitive.


伪类可以和 css 配合使用
```
a.highlight:hover {
    color: #ff0000;
}
```

Hover 可以在其他元素上使用

```
div:hover {
    background-color: blue;
}
```
并且创建类似 tooltip 的形式

```
p {
    display: none;
    background-color: yellow;
    padding: 20px;
}

div:hover p {
    display: block;
}
```
---
#### The :first-child Pseudo-class

**:first-child** 是选择第一个子元素，需要配合元素理解，比如 `p:first-child` 它的意义是首先是一个 p 元素，而且这个 p 元素还是某个元素的第一个子元素， 也就说任何元素的第一个子元素是 p

```
<div>
  <p>...</p>
</div>
```
下面使用 first-child 的各种情况

the selector matches any `<p>` element that is the first child of any element:

```
p:first-child {
    color: blue;
}
```
the selector matches the first child `<i>` element in all `<p>` elements:

```
p i:first-child {
    color: blue;
}
```
matches all `<i>` elements in `<p>` elements that are the first child of another element:
```
p:first-child i {
    color: blue;
}
```

同样还有 **:last-child**

---

**:first-of-type** 是选取第一个特定类型的元素，而不是第一个子元素，比如 `p:first-of-type` 选取某个父元素里子元素中的第一个 p 元素

```
<body>
  <div>
    <span>one</span>
    <p>The first paragraph.</p>
    </div>
    <p>The first paragraph.</p>
    <p>The second paragraph.</p>
    <p>The third paragraph.</p>
    <p>The fourth paragraph.</p>
</body>
```
`p:first-of-type` 会选取 body 和 div 的第一个 p 元素

1. 所以本质来讲 `p:first-of-type` 包含 `p:first-child`，

2. 而且更好理解，它是第一个特定类型的元素，可以是第一个元素也可以不是。

3. 注意他不一定是子元素，只要是后代元素就行

**:last-of-type**

---

**:nth-child selector**

- :nth-child(n)
- :nth-last-child(n)
- :nth-of-type(n)
- :nth-last-of-type(n)

可以选取重复的内容

关于 **:nth-child(n)** 的 **n** 的取值

1. n 是数字时，选取第 n 个元素
2. an + b 公式
  - 3n 那么选取 3，6，9...
  - 3n + 2 选取 2，5，8...
3. 奇偶 使用 odd/even
4. 负数
  - -2n + 10 选取 10，8，6，4，2

负数形式可以用 last 类配合公式解决来解决

默认情况下 **:nth-child(n)** 针对所有子元素，如果有其他多种元素存在，而且排列不规律，就要要选择 **:nth-of-type**

`div:nth-of-type(5)`  
`div:nth-of-type(2n)`  
`p:nth-of-type(even)`  

---

类似的

- :nth-last-child(n)
- :nth-of-type(n)
- :nth-last-of-type(n)
- :nth-last-child(n)
- :only-of-type 父元素只含有一个特定类型的元素
- :only-child 父元素只有一个子元素

- :not(selector) 除了括号里的元素
- :empty 选取某个空元素
- :lang(language) lang是全局属性，可以添加到任意的元素上
- :root 选取根元素 Html

---

下面的是 input 伪类

- :checked 选取 checked 属性的 input 控件
- :disabled
- :enabled 选取所有 enable 的 input，也就是没有 disable 的 input
- :focus
- :in-range 选取 value 在特定范围的 input
- :out-of-range 选取 value 超出特定范围的 input
- :invalid
- :valid 选取 value 值是 valid 的 input
- :read-only
- :read-write 选取没有 readonly 属性的 input
- :required
- :optional 选取没有 required 属性的 input

---

- :link 默认式样没有点击之前
- :visited 点击之后和 link 相对，表示这个链接之前点击过
- :hover 悬停式样
- :active 点击的时候，就在点击一瞬间或者按住不放时的式样
- :target 它会选择页面内跳转时 active 状态下 a 元素所关联的元素

<mark>伪类一定要配合元素实现准确的定位，以免造成冲突</mark>
<mark>父元素 元素 : 伪类</mark>

---

#### focus - input

所有元素
```
:focus {
  outline: 1px solid blue;
}
```
```
a:focus{
  outline: 1px solid blue;
}
```

有一个比较有意思的属性可以添加在文本的标签上 `contenteditable`,可以添加修改内容。

这个时候就需要 focus 伪类提醒用户在这里你可以修改。

```
input[type = "text"]:focus{
  background:yellow;
}
```
---
#### form element states

```
input:checked{
  ...
}

input:enabled{
  ...
}

input:disabled{
  ...
}
```

#### fragment identifier **#**

页面内跳 interior navigation 转时出现的问题，跳转时会出现位置不准确，所以需要对跳转的内容有所提示

**:target**
```
section:target {
  background:...
}
```
---

#### structural selector 结构选择器

#### child elements

- :first-child
- :last-child
- :only-child

意义在于在父元素中找到第一个子元素，或者最后一个子元素，冒号前的选择器相当于筛选器。

#### children by type

- :first-of-type
- :last-of-type
- :only-of-type

child 选择器的扩展 首先也是必须有一个容器元素，type 选择器不一定是子元素，可以是任意后代元素。所以是在这个容器找到第一个或者最后一个复合类型的元素。

#### only

only 的意义在于 first 和 last 必须是在多于一个元素的前提下， 针对只有一个元素的情况使用 only

#### empty

1. 有时候你可以检测是否你的代码中有不必要的空元素，给空元素一个式样
2. 表格常常会有空的单元格可以设置式样

#### Negation selector

**:not()**

- :not(p)
- p:not([class])
- li:not(:last-child)

可以配合属性选择器和伪类

需要非常准确，否则会造成意想不到的结果，因为会对目标元素以外的所有元素施加效果，包括一些容器元素（父元素），而对于没有设定式样的元素他就会继承父元素。

#### Combining selector

伪类之间和伪类与元素的结合,伪类的结合使用 chain 的方式，不用添加任何空格

```
h4:first-child:only-type-of{

}

p:not(:only-type-of):last-of-type::after{

}

a.current:first-child:hover{

}
```
不要过度使用，只是针对特别情况
