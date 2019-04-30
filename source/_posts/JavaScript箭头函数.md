---
title: JavaScript箭头函数
top: 2
copyright: true
date: 2019-04-30 14:53:27
categories:
- 理论
- 编程语言
- JavaScript
tags:
- JavaScript
- 编程语言
- 箭头函数
- 作用域链
---

### 一、什么是箭头函数

JavaScript箭头函数是 ECMAScript 6中引入的编写函数表达式的一种简便方法。

<!--more-->

例如：

```javascript
x => x * x
```

它相当于：

```javascript
function(x){
    return x*x;
}
```

### 二、要注意的问题

1. 箭头函数没有自身的this指针，其共用作用域链中最后一个this指针（一般是该函数声明处环境的this指针）。