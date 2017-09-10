---
layout: post
title:  "Css Animation"
date:   2017-08-28
tags: [Css Animation]
---

这篇主要是根据 Val Head 的教程来总结的，她自己也有自己的网站，可以去看看。

Css Animation 有三个概念， 三个概念有时候相互使用，容易混淆。本篇主要是使用 keyframe animation，下面对每一个进行介绍。

- transition
- transform
- keyframe animation

现在写 Css Animation 不需要在写前缀，几乎所有的主流浏览器对动画支持的很好

#### Transform

> Transform change the shape and position of the affected content by modifying the coordinate space.

所以 transform 改变的是 **形状** 和 **位置**

> Transform do not disrupt the normal document flow

<mark>这是非常重要的一点，transform 并没有改变文档流，也就说使用 transform 时页面的其他元素不会受到影响改变其原有的位置</mark>

```
.robot{
  transform: translateX(200px) skew(20deg) scale(2) rotate(45deg)
}
```

1. 多个 transform 属性可以写成上面的形式

2. 首先 translate 中的单位还可以使用 rem 和 %  注意使用百分比时并不是容器元素的百分比，而是目标元素自己 width height 的百分比

3. 属性的顺序不同，动画最终效果不同，应该跟元素的起始定位点有关，如果旋转不在元素中心那么后续的属性不导致不同的效果。

#### 3D Transform

3D Transform 必须先设置 <mark>perspective</mark>，设置方式有两种
- 添加在容器父元素上（推荐）
- 直接写在 transform 的属性中

```
.wrapper{
  perspective: 1000px;
}
```

1. perspective 可以使用单位 px 和 em， 表示你和物体之间的距离，

2. <mark>1000px</mark> 是一个中性值，近似于我们眼前的物体。

3. translate3d 中 z 的值 正值靠近你，负值远离你。

#### Transition

Transition 确实可以实现动画效果，但是和 Keyframe Animation 不同它是两个状态之间的变化。

- beginning state
- ending state （hover/active/...）

```
button {
  background-color: yellow;
}

button:hover {
  background-color: red;
  scale(1.2);
}
```
上面的代码没有设置 transition 属性 会直接跳转到最终属性，所以 transition 属性是控制动画效果的。

```
button {
  background-color: yellow;
  transition: background-color .5 ease , transform .5 ease-in-out .25;
}

button:hover {
  background-color: red;
  scale(1.2);
}
```
1. transition 属性添加到元素的初始状态中去。
2. transition 控制动画的时间效果的
3. transition 中可以写要添加动画的多个元素
4. transition 可以控制 transform 的呈现效果


#### Animation

keyframe animation

首先要有一个 Html structure

- wrapper  
- material

然后 keyframe animation 由两部分组成

- define the animation (设置动画要做什么)
- assign it to specific element/elements （分配给元素）

顺序可以任意，最好是先定义，然后分配

**@keyframe**

> Keyframe are a list describing what should happen over the course of the animation

下面是 keyframe 的 css 的示例

关键词 **@keyframes** 有 **s**

```
<!-- setup the animation -->
@keyframes slide {
  from { transform: translateX(0); }
  to { transform: translateX(900px); }
}

<!-- assign the animation slide to the element  -->
.robot {
  animation-name: slide;
  animation-duration: 2s;
  animation-timing-function: ease-in;
  animation-iteration-count: 1;
}
```

1. keyframe 动画有两种形式 from/to 和 % 如果只是简单两个状态的动画，使用 from/to 就可以了

2. 上面元素使用最常见的几种 animation 属性。需要施加的 **动画名称** **持续时间** **时间方程**  **循环**

**animation-delay** 延迟 没有什么特别的

#### **animation-fill-mode**

描述元素在 outside of the duration of animation 时的状态，也就是动画开始之前和结束之后时的状态。

- none 可能出现跳帧 闪现
- forwards 结束时保留在最后一帧，否则动画返回第一帧
- backwards 开始时保留在第一帧，无论之前元素的位置，比如下面的代码，会保留在 0% 的位置，比元素自己的位置移动了 100px；
- both 开始在第一帧，结束时在最后一帧

**both** 不是很好理解，它解决了跳帧的问题，看下面的代码

```
@keyframes {
  0% { transform: translateX(100px) rotate(0turn);}
  20% { transform: translateX(-10px) rotate(-0.5turn);}
  100% { transform: translateX(450px) rotate(2turn);}
}
```

![animation-fill-mode](/images/2017-08-28-Css-Animation-2-1.jpg)

#### Css rotate units

上面的 rotate 代码使用了特别的单位

- deg
  - Represents an angle in degrees. One full circle is 360deg. Examples: 0deg, 90deg, 14.23deg.
- grad
  - Represents an angle in gradians. One full circle is **400grad**. Examples: 0grad, 100grad, 38.8grad.
- rad
  - Represents an angle in radians. One full circle is **2π** radians which approximates to **6.2832rad**. 1rad is 180/π degrees. Examples: 0rad, 1.0708rad, 6.2832rad.
- turn
  - Represents an angle in a number of turns. One full circle is **1turn**. Examples: 0turn, 0.25turn, 1.2turn.


1. 正值是顺时针，负值逆时针
2. 从 负Y轴 开始算，
3. rad 一周是 2pi 但是要使用数字，也就是 6.2832rad

![rotate units](/images/2017-08-28-Css-Animation-2-2.jpg)

#### **animation-direction**

- normal
- reverse
- alternate 第一次正向 然后负向
- alternate-reverse 第一次负向 然后正向

其中后两个 animation-iteration-count 必须大于 1

**animation-direction** 描述了 keyframe 的执行顺序

#### **animation-timing-function**

**animation-timing-function** 接受三种参数

- predefined keywords
  - ease 默认
  - linear
  - ease-in
  - ease-out
  - ease-in-out
- cubic-bezier function
  - cubic-bezier(x1,y1,x2,y2) 两个控制手柄的坐标位置
- steps

[cubic-bezier](http://cubic-bezier.com/#.17,.67,.83,.67)参考网站

要理解 cubic bezier 曲线，陡峭说明加速，平缓说明匀速

#### multiple animation

```
@keyframes slideIn {
  0% {
    transform: translateY(400px);
    animation-timing-function: ease-out;
  }
  60% {
    transform: translateY(-50px);
    animation-timing-function: ease-in;
  }
  80% {
    transform: translateY(10px);
    animation-timing-function: ease-out;
  }
  100% {
    transform: translateY(0);
    animation-timing-function: ease-in;
  }
}

@keyframes fadeIn {
  from {opacity:0;}
  to {opacity: 1;}
}

section {
  animation: slideIn .8s linear, fadeIn .2s ease-in;
}

```

1. 0% 的初始位置总是远离元素最初位置，才能达到归位的效果

2. 每个百分比都可以分别写入 animation-timing-function 等属性

3. 100% 写入的属性 比如 animation-timing-function 属性，在使用 reverse 等设置才会生效，单一的过程会忽略。

4. 多个动画可以加入到同一个元素，但是必须是不同属性，比如上面的 transform 和 opacity

5. transform 包含多个属性 比如 translate rotate 必须写在一起，否则以第一个 transform 的属性为准，其他的忽略，不能把他们分开写写成两个 transform。

6. 多个动画，注意延迟，所有动画都是以同一个时间点开始的

7. 多于两个动画建议用 javascript/sass 来写

8. 复杂动画最好分开来写容易控制参数

例子参照[Chian Multiple Animations](https://www.lynda.com/CSS-tutorials/Chain-multiple-animations/439683/461540-4.html?autoplay=true) 并查看它的源码

#### **animation-play-state**

- paused
- running

需要结合 hover 等 trigger 使用创造效果，比如先在元素上设置animation-play-state: paused， 在 hover 中设置 running，那么只有悬停在元素上才会触发动画。

#### 3D transform

这里主要是讲述 3D rotate

1. 首先设置 perspective
2. html 结构需要对每一个元素添加标签好施加动画，并且添加延迟。
3. 由于旋转默认在每个元素的中心，所以还要设置，transform-origin
4. transform-origin 默认 50% 50%，是元素的宽高的百分比，而不是父元素，而且 transform-origin要放在元素上。
5. 例子中对文字设置 rotate 使用了 50% 70%， 因为文字下面还有一些空白

#### Steps

animation-timing-function: steps(10);

steps 把一个动画分成几步来执行，类似于创建逐帧动画。


#### SVG

- 使用独立图形
- 考虑好图形在空间中的关系
- 文字使用 live text 还是 outline text
- 使用 illustrator 做好每个图层的命名
- 使用 [SVG Editor](https://petercollingridge.appspot.com/svg-editor)优化代码

现在使用的是 svg 1.0 有很多属性 css 并不支持，所以为什么会使用 js，因为 js 可以引导更多属性

常用的 svg 属性

- fill
- opacity
- css transform

**transform-origin** 的不同

- html 以元素的中心为基准
- svg 以 canvas 的左上角为基准

有两个 svg 的 javascript 库

- [greensock](https://greensock.com/)
- [snap](http://snapsvg.io/)

#### 各种动画的适用场景

1. keyframe animation： 简单的线性动画，简单的几种状态改变

2. Transition：适合 toggle 两种状态

3. Javascript： 复杂的状态，动态动画，模拟物理量。

技术结合

- js + css
- js/css + svg

#### online tool

- [cubic-bezier](http://cubic-bezier.com/#.17,.67,.83,.67) tool
- [ease function](http://easings.net/)
- [bounce.js](http://bouncejs.com/)
- [SVG optimizer](https://petercollingridge.appspot.com/svg-editor)

#### dev tool

chrome
- 可以查看编辑 cubic-bezier
- 更多工具 animation 加载点击 animation 可以编辑 animation 查看效果
