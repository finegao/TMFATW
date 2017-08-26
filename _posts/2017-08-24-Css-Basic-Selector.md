---
layout: post
title:  "Css Basic Selector"
date:   2017-08-24
tags: [Css selector]
---

#### 元素选择器

元素选择器的优先级非常低，所以是一个覆盖重写文档样式非常有效的一个策略，他不会影响高优先级，那些重要元素的式样。但是要注意，他会对整个页面进行修改，所以要对 **整体式样** 修改时选用它非常好。所以一般来说要先用元素选择器设置网站的基本式样。

#### Class

Class 可以重复使用，并且可以提供语义，比如 .warning,也可哟配合元素选择器使用，但是过多的使用会导致代码非常难读，所以还是要尊重 html 的语义来减轻 css 的负担。

#### Id

Id 选择器必须是页面当中唯一的元素式样，不可以重复使用。大多数人不愿使用因为优先级太高，不利于后面的代码的 overwrite 针对小项目似乎比较合适，需要合理的使用，考虑好之后修改的情况。同样可以和 **元素选择器** 配合当做 **后代选择器** 使用

#### Descendent Selector

后代选择器

element element ... ： div p

也可以嵌套多层 div p span .class

理解后代选择器有一个问题就是到底是哪一个后代，比如 div p， 他实际会找到所有的后代，无论元素嵌套的多深,比如下面 div 里 p 无论在哪都会被找到。

```
<div>
  <header>
    <p>
  </header>
</div>
```

```
<div>
  <p>...</p>
  <header>
    <p>...</p>
  </header>
</div>
```

后代选择器配合 class 或者 id 使用可以更加准确的选择元素，元素之间的配合更适合设置基本式样。

- .class p (基本)
- div p .class (准确)

但是要避免写多重的嵌套的后代选择器

#### Universal selector

*

它会选择所有的元素，适合 css reset 或者 setting default 比如设置 <mark>box-sizing</mark>，参考 Eric Meyer 的 base css。

全局选择器没有优先级，所有有冲突的式样都会覆盖它，浏览器默认式样除外。

浏览器对某些元素有默认式样，所以想要改变式样直接添加相应的式样就好了。

#### Grouping selector

element，element，element

所有元素包括伪类，同样组选择器经常设置全局式样，一般会写在 css 文件的最前面去除某些元素的 margin/padding，改变一些元素的 display。

而且很方便改写，比如下面的例子，如果想改写某个单独元素只需要在组选择器后面改写就好了
```
h1,h2,h4,h6{
  color:red;
}

h2{
  color:green
}
```
---

#### Combinator

#### 直接子元素选择器

element1 > element2

`div > p` `article > section > h2`  

和后代选择器不同，它只会选中子元素，而且是父元素中所有同类型的子元素,其他嵌套在更深层次的元素不会被选中。

#### Sibling selector

element1 ~ element2

`div ~ p ~ blockquote`

兄弟选择器，它是选中所有 element1 之后所有的 element2 类型的兄弟元素，也就是说

1. 元素1、元素2必须同级，也就是说必须是同一个父元素，无论嵌套在多深。
2. 必须是元素1之后的元素2，之前的元素2没有效果
3. 所有的

#### Adjacent sibling

element1 + element2

`h3 + p + p`

相邻兄弟选择器，会选择 element1 后相邻的第一个兄弟元素 element2

1. 必须是 element1 后面
2. 必须相邻，中间有其他元素，失效
3. 兄弟元素，同一个父元素
4. 只选取一个元素


---

#### Attribute selector

使用标签元素的属性定位元素来设置式样

`[attribute]{...}` `[class]` **所有有 class 属性的元素**

`element[attribute]{...}` `div[class]` <mark>注意元素和属性选择器之间没有空格</mark>

可以使用 class 定位元素，同时属性选择器可以结合元素形式寻找特定元素下的复合属性的元素

有时候属性选择器可以通过设置 border 然后观察页面 来检测哪些元素有设置的属性，哪些元素没有

#### Attribute value

选择属性值匹配的元素  
`[attribute = "value"]` `[class = "tip"]`

选择当有多个属性值时，包含这个属性值的元素  
`[attribute ~= "value"]` `[class ~= "tap"]`

比如下面这个元素只会被第二个选中  
`<div class = "tip tap" title = "one two">`

常用第二个选择器的属性有 **class**， **title**，**alt**

**title** 的名字也可以看做属性值，所以只要有空格就可以使用第二属性值选择器，选择名字中字符串的一部分。

#### String match

- match prefix
```
a[href ^= "http://"]{
  ...
  }
```
- match suffix
```
a[href $= ".pdf"]{
  ...
  }
```
- match partial string
```
p[class *= ".pdf"]{
  ...
  }
```

上面都是各个选择器经常配合的元素，但是可以单独使用，只是要避免冲突。
