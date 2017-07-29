## 总结javascript难点
### 1.立即执行函数
  立即执行函数，即Immediately Invoked Function Expression(IIFE),正如它的名字，就是创建函数的同时立即执行,它没有绑定任何事件,也无需要等待任何异步操作
   ```javascript
   (function() {
     // 代码
     // ...
    })();
   ```
 function(){...}是一个匿名函数,包围它的一对括号将其转换为一个表达式,紧跟其中的一对括号调用了这个函数.立即执行函数也可以理解为立即调用一个匿名函数。立即执行函数最常见的应用场景就是:将var变量作用域限制于你们函数内，这样可以避免命名冲突
