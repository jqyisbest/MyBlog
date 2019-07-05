---
title: JavaScript入门---01
top: 2
copyright: true
date: 2019-07-04 17:20:20
categories:
- 女友学编程
- JavaScript
tags:
- 女友学编程
---

JavaScript 是一门语言，和英语一样。英语用于人与人之间的交流，而JavaScript用来和Web前端交流。

<!--more-->

>并不是说JavaScript只能用在前端，现在有JavaScript来写后端代码的框架，但JavaScript的大部分用法还是用于前端。

Web前端主要包括浏览器、网页等等。这意味着你可以通过JavaScript**操纵网页和从浏览器获取数据**。比如你可以通过JavaScript在网页上显示一个弹窗。

```javascript
window.alert("你好");
```

通过写入这条语句，网页上就会显示一个内容为“你好”的弹窗。

那么，在哪里写入这条语句呢？

先告诉你结论，**JavaScript脚本应该写在HTML代码的*`<script></script>`*标签中。**

我们先来看下在你双击打开一个*.html*文件的时候发生了什么。

> 双击.html文件 => 浏览器读取html文件为一串文字 => 浏览器按照文字中的内容来显示网页

不是什么文字都能被浏览器显示成网页的，遵从某种语言的语法的文字才能被能被浏览器显示成网页。而这种语言，叫做*超文本标签语言*，简称**HTML**。*.html*文件就是一个包含了HTML文字的文件，这个文件在浏览器中会被显示为一个网页。

那么，HTML和JavaScript是什么关系呢？

这里引用一句其它教程里的话：

>JavaScript 是属于 web 的语言，它被设计为向 HTML 页面增加交互性。

如果你只是想在网页上显示你好，那么完全不需要JavaScript。

如果你想以动态的方式显示你好，那么光有HTML是不够的。

