---
layout: post
title:  "Css Transition and Transform"
date:   2017-08-26
tags: [Css Animation]
---

#### Css Transition

<mark>CSS3 transitions allows you to change property values smoothly (from one value to another), over a given duration.</mark>

所以 Css Transition 就是在一段时间里改变某个 css 属性

#### Fundamental

To create a transition effect, you must specify two things:

- the CSS property you want to add an effect to
- the duration of the effect

<mark>Note: If the duration part is not specified, the transition will have no effect, because the default value is 0.</mark>

#### Property

- transition 是下面四个属性的简写
- transition-delay
- transition-duration
- transition-property
- transition-timing-function

例子  
`transition: width 2s;` 属性 / 时间  
`transition: width 2s, height 4s;` 更改多个属性

#### **transition-timing-function** 属性

- **linear**	规定以相同速度开始至结束的过渡效果（等于 cubic-bezier(0,0,1,1)）。
- **ease**	规定慢速开始，然后变快，然后慢速结束的过渡效果（cubic-bezier(0.25,0.1,0.25,1)）。
- **ease-in**	规定以慢速开始的过渡效果（等于 cubic-bezier(0.42,0,1,1)）。
- **ease-out**	规定以慢速结束的过渡效果（等于 cubic-bezier(0,0,0.58,1)）。
- **ease-in-out**	规定以慢速开始和结束的过渡效果（等于 cubic-bezier(0.42,0,0.58,1)）。
- **cubic-bezier(x1,y1,x2,y2)**	在 cubic-bezier 函数中定义自己的值。可能的值是 0 至 1 之间的数值。
- **step-start**
- **step-end**
- **steps(<integer>[, [ start | end ] ]?)**

有关于 ease 之间的区别参照 [Css Trick](https://css-tricks.com/ease-out-in-ease-in-out/)，还有关于 [Easing Functions](https://github.com/ai/easings.net) 的参考

transition 可以和 transform 结合使用

---

**hover** 本身也是一种 **transition** 但是不受控制，动画效果是自动的。

```
a {
  background-color: orange;
  transition-property: background;
  transition-duration: 1s;
}

a:hover {
  background-color: blue;
}
```

所以一般来说 transition 有两个部分组成

- always add transition declarations to initial state
- trigger states

首先要选定元素的初始状态的一些属性施加 **transition** ，第二要有一个 **trigger**。

一般的 **trigger** 有：
- :hover 悬停
- :focus
- :active 点击
- :target
- :checked
- :disable

哪些属性可以施加 transition，[W3C](https://www.w3.org/TR/css3-transitions/#transition-property-property) 提供的参考列举了所有可以 **transition** 属性

#### Vendor prefix

- -webkit- (Chrome, Safari, newer versions of Opera, almost all iOS browsers (including Firefox for iOS); basically, any WebKit based browser)
- -moz- (Firefox)
- -o- (Old, pre-WebKit, versions of Opera)
- -ms- (Internet Explorer and Microsoft Edge)

所以为了兼容更多的浏览器，更多时候会写成下面的形式
```
-webkit-transition-property: color;
-moz-transition-property: color;
-o-transition-property: color;
-ms-transition-property: color;
transition-property-property: color;
```

随着浏览器的不断更新，无前缀CSS代码得到越来越完整的支持。Chrome 26+，Firefox 16+，Opera 12.10+，IE 10+几乎都已经不再需要CSS前缀了，因为它们支持无前缀的CSS代码。

-ms-: 貌似从来没有一个稳定的IE支持-ms-前缀，这些知识在IE预览版中使用的（稳定版的 IE 10既支持有-ms-前缀的CSS代码也支持无前缀的CSS代码）。所以，我们写CSS代码的时候，-ms-是没有必要添加的。

-moz-: Firefox 3.6 – Firefox 15 （占全球约4%的用户）还需要使用-moz-前缀，但是，如果你只是添加了一个渐变阴影之类的，那就没有必要用-moz-了。更多情况下， 还是加上为妙。

-webkit-: 最新版的Chrome已经没有采用webkit内核了，但是Safari一直是采用的webkit，并且，几乎所有的移动浏览器都使用webkit，所以，我们还得继续使用-webkit-。

-o-: 只有低于Opera 12.10的版本还需要-o-前缀，全球大概只有0.25%的用户使用Opera 12.10或小于此版本的Opera浏览器，并且，Opera Mini一直都不支持-o-，所以，大多数情况下，我们没有必要使用-o-。

我的建议是，不要使用-ms-，没有明确的要求的话也不要使用-o-，-moz-和-webkit-还是需要的。当然，为了简单也可以使用-prefix-free。

所以可以简写为
```
-webkit-transition-property: color;
-moz-transition-property: color;
transition-property-property: color;
```

---

#### transition option

ease 和 ease-in-out

![ease](/images/transition1.jpg)

esae 的中间部分更快

---

cubic-bezier

cubic-bezier（x1,y1,x2,y2）: x y 的取值在 0 到 1 之间，一组 x y 代表了 bezier handle 的位置

---

transition-delay 和 transition-duration 可以使用的时间单位 s / ms

---

#### 2D transform

<mark>CSS3 transforms allow you to translate, rotate, scale, and skew elements.
A transformation is an effect that lets an element change shape, size and position.
CSS3 supports 2D and 3D transformations.</mark>

所以 transform 可以改变 形状/大小/位置，主要用于 div img 等标签

- translate(x,y)
- translateX(x)
- translateY(y)
- rotate(deg)
- scale(x,y) 根据 x y 方向上扩大的倍数
- scaleX(x)
- scaleY(y)
- skew(degX,degY) 角度接受负值
- skewX() x 方向上的斜切
- skewY()

- matrix() matrix(scaleX(),skewY(),skewX(),scaleY(),translateX(),translateY())

#### transform syntax

transform: function(parameters);

方程就是上面给出的方程

---

**transform-origin** 根据元素上的位置来的，50/50 就是元素的中心，0/0就是元素的左上角，接受负值/px/关键词

- transform-origin: 50% 50% 默认 元素中心
- transform-origin: 10px 0
- transform-origin: left bottom

---

#### 使用 Css transform 之前

使用 css transform 之前，可能要做一些提前的设置，对于 2D 可以直接使用，但是 3D 必须进行一些设置。 具体可以参照 [Using CSS transforms](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transforms/Using_CSS_transforms)

**2D** transform 使用前的设置

**transform-origin** 可以根据具体情况使用，默认是元素的中心位置。

---

**3D** transform 使用前的设置

<mark>3D transform 使用前要 包含3D元素的容器元素 div 设置 perspective</mark>
Setting up a perspective，有两个属性要提前设置，这两个属性都是针对 perspective 的

- perspective 设置物体到观察者的距离，类似于景深，越小越远
- perspective-origin 设置观察者的位置，从平面的那个角度观察, 50/50 是默认值

- translate3d(x,y,z) z 的值 正值靠近 负值远离  
- scale3d(x,y,z,a) 前三个值是表示各自方向上的向量，结合之前那的 perspective-origin 得到一个方向，a 的值表示旋转角度，正值顺时针，负值逆时针。比如 `transform: rotate3d(1,2,2,15deg)`

**transform-style**

> The transform-style CSS property determines if the children of the element are positioned in the 3D-space or are flattened in the plane of the element.

**transform-style** 是决定子元素的显示方式

- preserve-3d 使用 3d
- flat 使用 2d

---

#### 实例

#### 改变颜色

```
a {
  display:block;
  background-color: red;
  -webkit-transition: background-color .75s ease;
  -moz-transition: background-color .75s ease;
  -o-transition: background-color .75s ease;
  transition: background-color .75s ease;
}

a:hover{
  background-color: rgba(r,g,b,a)
}
```

1. 注意元素的初始状态下添加 transition 选取要改变的属性，并且设置时间方式
2. transition 可以添加的属性有四个：目标属性/持续时间/时间方程/延迟时间，其中延迟时间可以不添加，各个属性用空格隔开。多个属性用逗号分隔。
3. 触发控件中添加要改变属性的值

#### fading

使用 opacity 属性
```
.status h3{
  position:absolute;
  top: 0;
  opacity: 0;
  -webkit-transition: opacity .75s ease-in;
  -moz-transition: opacity .75s ease-in;
  -o-transition: opacity .75s ease-in;
  transition: opacity .75s ease-in;
}

.status:hover h3{
  opacity: .8;
}
```
opacity 使用了类作为添加的方法

<mark>以及 hover 的用法，当我们想 hover 一个大元素时并且改变小元素，使用下面的选择器</mark>  
`
div:hover p
`
#### growing

使用 scale 方程扩大 width 和 height,这里 transition 配合 transform 使用，单独使用 transition 改变大小首先需要定位，否则都是从左上角开始，而且元素的大小改变会影响周围的元素，transform没有这个问题，默认从中心开始，而且不会影响周围元素，但是 transform 单独使用时动画是即时的没有缓慢效果，所以 transition 和 transform 配合使用达到元素突出从中心变大的效果。

```
img {
  width:180px;
  height:180px;
  -webkit-transition: all .5s ease-in-out;
  -moz-transition: all .5s ease-in-out;
  -o-transition: all .5s ease-in-out;
  transition: all .5s ease-in-out;
}

img:hover{
  -webkit-transform:scale(1.2);
  -moz-transform:scale(1.2);
  -o-transform:scale(1.2);
  transform:scale(1.2);
}

```

注意 transition 代码中使用了 属性 all 选取所有选择器中的属性，所以某种意义上 transform 相当于一种最终状态，而 transition 相当于控制达到最终状态的各种效果。上面的例子还可以加入 box-shadow 属性增加立体感。

这里提到了另一个属性 **backface-visibility** 是描述旋转时，当背面面向用户时，是否显示内容。

改变大小还可以用在按钮等元素，提高用户体验。

#### spin

需要沿着 y 轴旋转，所以需要 rotateY，所以首先要设置 perspective
```
#outerWrapper{
  width:1000px;
  margin:30px auto;
  position:relative;
  -webkit-perspective:500px;
  -moz-perspective:500px;
  perspective:500px;
}

#logo {
  position:absolute;
  -webkit-transition: all 2s ease;
  -moz-transition: all 2s ease;
  transition: all 2s ease;
}

#logo:hover{
  -webkit-transform: rotateY(360deg);
  -moz-transform: rotateY(360deg);
  transform: rotateY(360deg);
}
```
transition 的 all 属性是施加于所有可以有 transition 效果的属性

要使logo在页面加载是自动旋转需要使用 jquery 在页面加载完成后给目标元素添加一个 transform 的类，这个类只要包含 transform 的方程就可以了。

#### 放大字体

使用 font-size 属性

---

#### Transition multiple properties

使用分开的写法,注意 transition 和 transform 的关系

```
.wheel{
  opacity:.2;
  -webkit-transition-property:left,opacity,webkit-transform;
  -webkit-transition-duration:3s,4s,3s;
  -webkit-transition-timing-function:ease,ease,ease-out;
  -webkit-transition-delay: 0s,.5s,0s;

  -moz-transition-property:left,opacity,moz-transform;
  -moz-transition-duration:3s,4s,3s;
  -moz-transition-timing-function:ease,ease,ease-out;
  -moz-transition-delay: 0s,.5s,0s;

  transition-property:left,opacity,transform;
  transition-duration:3s,4s,3s;
  transition-timing-function:ease,ease,ease-out;
  transition-delay: 0s,.5s,0s;
}

.anim-wheel{
  opacity:1;
  -webkit-transform:rotate(-1080deg);
  -moz-transform:rotate(-1080deg);
  transform:rotate(-1080deg);

}
```

#### CSS Animation

动画部分，与之前的不同这里使用 keyframe，而且之前的 Transition 和 transform 只能从一个状态到另一个状态，而 animation 可以在不同时间点下转化多个不同状态。另外不需要 js 就可以自动播放。

#### The @keyframes Rule

动画由两部份组成

- keyframe
- 绑定元素

from to 的写法

```
/* The animation code */
@keyframes example {
    from {background-color: red;}
    to {background-color: yellow;}
}

/* The element to apply the animation to */
div {
    width: 100px;
    height: 100px;
    background-color: red;
    animation-name: example;
    animation-duration: 4s;
}
```
百分比写法

```
/* The animation code */
@keyframes example {
    0%   {background-color: red;}
    25%  {background-color: yellow;}
    50%  {background-color: blue;}
    100% {background-color: green;}
}

/* The element to apply the animation to */
div {
    width: 100px;
    height: 100px;
    background-color: red;
    animation-name: example;
    animation-duration: 4s;
}
```
- @keyframe 要添加 动画名字
- 可以在 keyframe 里写多个属性用 **分号** 隔开
- left 属性是对元素定位是 relative 或者 absolute 使用的

元素上可以添加的属性

- animation-name: example; （必填）
- animation-duration: 5s;（必填，否则认为是 0 没有效果）
- animation-timing-function: linear; （与 transition 相同）
- animation-delay: 2s;
- animation-iteration-count: infinite/数字
- animation-direction: normal/reverse/alternate; 其中 alternate 是每个周期改变一次方向

简写形式：`animation: example 5s linear 2s infinite alternate;`

另外还有两个属性

- animation-fill-mode:forwards/backwards 描述动画结束后停留在哪个状态，初始还是结束时的状态
- animation-play-state:paused/running 控制动画播放状态

针对不同的浏览器
```
@-webkit-keyframes spotlightBG{
  0% {background-color:red};
  25%
  50%
  75%
  100%
}

@-moz-keyframes spotlightBG{
  ...
}

@-keyframes spotlinghtBG{
  ...
}

div {
  background-color:red;
  -webkit-animation:spotlinghtBG 10s infinite alternate;
  -moz-animation:spotlinghtBG 10s infinite alternate;
  animation:spotlinghtBG 10s infinite alternate;
}
```
[Ceaser](https://matthewlein.com/tools/ceaser)是一个 Ease Animation 模拟器，可以生成代码，也可以上网查询其他的 Css 3 generator。
