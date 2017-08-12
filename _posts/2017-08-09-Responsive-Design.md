---
layout: post
title:  "Responsive Design"
date:   2017-08-09
tags: [Responsive Design]
---

### Responsive Design

Responsive Design 的三个方面

- Fluid Grids
- Media Query
- Flexible Media

## Viewport 理解

Viewport - Initial scale factor

Controlling the Viewport

1. # **Viewport Metatag**
2. # **Viewport CSS Rule**

1 Viewport Metatag
~~~~~~
<head>
  <meta name = "viewport" content = "width = device-width, initial-scale = 1">
</head>
~~~~~~
initial-scale = 1 是默认放大倍数

2 Viewport CSS Rule
~~~~~~
viewport{
  width:480px;
  zoom:1;
}
~~~~~~

由于优先级的问题，viewport应该放在media queries 的前面

其中width的设置
~~~~~~
width = device-width
~~~~~~

Viewport 的属性可以参照下面的链接  
[Using the viewport meta tag...][1]  
[css @viewport][2]  
[meta tags][3]  

移动设备尺寸参考  
[Mobile Matrices][4]

## 图片

利用svg或者css写成的图片在响应式布局中没有显示的问题，但是svg要比 bitmap/位图 要大

## Media Declaration

**media** 这是link的一个属性，包括如何在不同的设备上显示网页,比如print，screen，speech和all.
~~~~~~
<link rel = "stylesheet" href = "main.css" media = "screen">
~~~~~~
[link tag参考][5]

## Media Queries

Media Queries要配合相应的css文件以及link的media属性来使用，简单来说就是不同的尺寸的设备利用link的media属性来选择对应的css文件.
~~~~~~
<!-- CSS media query on a link element -->
<link rel="stylesheet" media="(max-width: 800px)" href="example1.css" />
<link rel="stylesheet" media="(max-width: 400px)" href="example2.css" />
~~~~~~
其中 breakpoint 的概念是响应式布局的触发点，要考虑好选取哪些尺寸来做 breakpoint.
![breakpoint](/images/responsive1.jpg)

------
下面这个链接是 media queries在MDN的详细参考，非常详尽。   
[Media Queries Ref][6]

## device-width and width

可以看到media queries 设置时都是用的 width，这是因为device-width是一个固定的值，它指的是设备宽度，横向像素的多少的一个数值，而width指的是
viewport 的大小是一个变动的值，会因为设备的变化或者操作而改变大小。而且由于设备的尺寸众多，使用width更加的稳定。

## 单位的选择

虽然使用width是不错的选择，但是使用 em 的趋势在不断增加,它所产生的问题更少，参照下面的链接。
~~~~~~
100% = 1 em ~= 16px ~= 14pt
~~~~~~
em 的问题在于要确定html的字体大小，默认是16px。然后根据html的字体大小设置media queries的大小.如果更改了
html字体的大小那么 em 也要随着改变。  

[media queries unit][7]


## fluid layout

页面设计时要会有column和gutter的概念，把页面分为传统平面设计中板式。
![fluid layout](/images/responsive2.jpg)

关于布局之后再bootstrap或者css布局中继续，此处没有技术。

## responsive image and media

传统的解决办法是把图片设置为弹性的大小，利用百分比或者相对单位。
问题是对于宽屏的大图片对于其他设备下载会产生影响
所以出现了两个解决办法
1. srcset属性
2. picture标签

srcset属性是img标签的一个属性，有时候会结合size属性来使用，注意srcset属性中会出现 w 这是一个标识符，代表width
就是图片的真实的像素大小，可以查看[img标签](8)的详细介绍，和[responsive image](9)的文章。

## CSS Unit
之前的讨论也涉及到了css中的一些单位，可以参看[css units][10]

[1]:https://developer.mozilla.org/en/docs/Mozilla/Mobile/Viewport_meta_tag
[2]:https://developer.mozilla.org/en-US/docs/Web/CSS/@viewport
[3]:https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta
[4]:https://github.com/h5bp/mobile-boilerplate/wiki/Mobile-Matrices
[5]:https://www.w3schools.com/tags/att_link_media.asp
[6]:https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries
[7]:https://zellwk.com/blog/media-query-units/
[8]:https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img
[9]:https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images
[10]:https://www.w3schools.com/cssref/css_units.asp
