---
layout: post
title:  "Particle.js"
date:   2017-08-24
tags: [JavaScript]
---

1. 首先去 Particle.js 的官网设置参数，然后下载参数的 json 文件

2 然后登陆 github

引入 particle.js 也可以使用 CDN，然后创建一个 id 为 particles-js 的容器

```
<div id="particles-js"></div>

<script src="particles.js"></script>
```
3 app.js

创建另外一个 js 引入 参数 json，不要忘记把这个 js 添加到页面中

```

particlesJS.load('particles-js',
'assets/particles.json';
});
```
其中 第一个参数就是页面中容器的 id，第二个参数就是下载的 json 数据，复制进去就好了。
