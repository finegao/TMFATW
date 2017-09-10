---
layout: post
title:  "Id and Class selector"
date:   2017-08-27
tags: [Css selector]
---
经常看到这样的写法，感觉很困惑
```
#one .two{
  ...
}
```

其实本质上 id 和 class 都是选择器，我们只是利用他们找到元素，所以拥有相同 class 的元素的式样不一定相同，上面的写法的意义只是找到 id 是 one 的父元素中 带有 class 是 two 的后代元素，然后施加式样，他并没有改写原有的 class。所以页面中有相同 class 的元素式样不一定相同，比如下面。

```
.two{
  color:red;
}

#one .two{
  color:blue;
}

<div class = "two">
...
</div>

<div id = "one">
  <div class = "two">
  ...
  </div>
</div>
```
---

```
#one .two{
  ...
}
```
所以上面的写法并没有改写原有 class 的式样，他只是找到 id 元素的中带有 class的后代元素然后给予式样。可以把这类写法看成是特殊的写法加以区分。

---

但是还是要避免这样写法，最好是每个相同名字的 class 就只是控制一类式样，为了避免上面的写法最好在创建一个其他名字的 class 给予元素。
