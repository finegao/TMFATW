---
layout: post
title:  "Markdown Reference"
date:   2017-08-12
tags: [Markdown]
---

## Markdown 参考

Atom 可以使用 Markdown 预览工具  
[StackEdit.io](1)是一个很好的Markdown在线编辑工具

注意，本质上每一段文字都是 inline元素，所以必须以 inline 的结构来思考，同时可以使用 span 标签添加文字，使用 i 标签添加图标，注意和图片的区别。参考[StackEdit.io](1)。

### i 标签

`<i class="icon-cog"></i>`  

 heading

\# 来表示 h1 \#\#\#\#\#\#表示 h6

注意 h1 是最大的，\# 越多标题越小

### 强调

使用 \* 和 \*\* 这个符号，并且不能用在开头，有待实验，


### 特殊字符

使用 \\ 来使用特殊的字符，使用它可以暂时退出Markdown占用的功能符号

### Html 标签

markdown 中可以随意插入 html 标签，并且添加 class  

### line break

回车产生的空白行就会自动产生自然段落，本质上是`<p>`标签

对于 inline 元素，要在结尾添加两个空格，本质上是`<br>`

### 背景色/代码行  

使用 tick mark 就是这个符号 \`， 在左上角数字一前面，加上背景色的本质是提供 code 标签,所以html元素就可以用这个符号表示，`<html>`

### 代码段 code block

之前利用 tick 可以产生代码行的效果，对于代码段，只要把代码段用三个以上的tick包裹，就可以产生代码段效果。

```
if (isAwesome){
  return true
}
```
### 引用 quote

使用 \> 产生引用效果

### 列表 list
使用 \- bash 来表示列表的分类，然后用缩进表示列表得层级。  
数字列表直接用数字表示就可以了。

### horizontal rule
用 tick 来表示代码，然后用三个 \- bash来表示分割线。
同时 bash 还可以来表示列表

### 图片
\! \[ alt \] \( url \)

### 链接

\[ 超链接文字 \]\( 数字或者链接的提示 \)
可以使用参考文字，有更好地提示作用，如果一个链接要使用很多次的话。  

\[数字或者链接的提示\]\:url
 注意不要忘记把标识用\[ \]括起来。

### 表格

使用 \| pipe 和 \- bash 来组合表格，也可以使用[markdown table generator](2)直接复制生成的表格。

### 其他
- [reveal.js](3)是一个利用markdown生成presentation的js库
- [master MD](4)一个很好地MD参考

[1]: https://stackedit.io/  
[2]: http://www.tablesgenerator.com/markdown_tables  
[3]: http://lab.hakim.se/reveal-js/#/
[4]: https://guides.github.com/features/mastering-markdown/
