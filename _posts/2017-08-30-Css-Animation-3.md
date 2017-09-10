---
layout: post
title:  "SVG Animation"
date:   2017-08-30
tags: [Css Animation]
---

这篇主要是根据 Sarah Drasner 的教程来总结的，可以查看她的 codepen 以及文章

#### SVG

前面都是 svg 的基本知识

#### SVG Optimization

[SVGOMG](https://jakearchibald.github.io/svgomg/)
[Svg-editor](https://petercollingridge.appspot.com/svg-editor) 这个有点老

<mark>SVG 对 inline元素 支持的比较好</mark>

css 动画对于复杂的图形需要大量代码，所以这时候 svg 可以大显身手。

#### SVG Sprites

- step animation
- fallback 备用，以防有些浏览器不支持 svg
  - modernizr
  - png
- grunticon:一个制作动画的工具
- 背景使用滚动， 前景使用 step 动画
- 对于 illustrator 产生的文件 使用 css 属性值选择器比较好
  - `[class ^= "star" ]`

#### performance

Testing tool - [jankFree](http://jankfree.org/)

#### greensock 简介

greensock 的 [ease-visualizer](https://greensock.com/ease-visualizer) 很棒

#### stagger

stagger 是一种每个元素做同样的动作，但是每一个都有一个相同的延迟

#### timeline

timeline 是最基础重要的部分

#### illustrator workflow

完成素材之后 直接复制代码到 svg optimizer 里面生成简化的代码 然后使用

#### UX/UI

[transform-icon](http://www.transformicons.com/)

#### Drawsvg

#### Motion along a Path

#### MorphSvg

**Resources**
- Codepen
