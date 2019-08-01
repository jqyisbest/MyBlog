---
title: Tips
top: 3
copyright: true
date: 2019-05-08 10:19:20
categories:
- 实现
- 常见错误
tags:
- 警告
---

一些重要的小细节，时常来看看省的忘记。

<!--more-->

**Java**

1. 开发中不使用sun.*的包，能避免很多坑。

**JavaScript**

1. 屏蔽浏览器错误输出及解除屏蔽

   ```javascript
     var defaultConsoleError=console.error;
     var defaultWindowError=window.error;
     function disableError() {
         //错误屏蔽
         window.onerror = function (value) {
           return true
         };
         console.error = function (value) {
           return true;
         };
       }
     function enableError(){
         //解除屏蔽
         window.onerror=defaultWindowError;
         console.error=defaultConsoleError;
       }
   ```

   

