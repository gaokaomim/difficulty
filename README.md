## 总结javascript难点
### 1.立即执行函数
  立即执行函数，即Immediately Invoked Function Expression(IIFE),正如它的名字，就是创建函数的同时立即执行,它没有绑定任何事件,也无需要等待任何异步操作
   ```javascript
   (function() {
     // 代码
     // ...
    })();
   ```
 function(){...}是一个匿名函数,包围它的一对括号将其转换为一个表达式,紧跟其中的一对括号调用了这个函数.立即执行函数也可以理解为立即调用一个匿名函数。立即执行函数最常见的应用场景就是:将var变量作用域限制于你们函数内，这样可以避免命名冲突。
 ### 2.立即执行函数
   对于闭包(closure),当外部函数返回之后，内部函数依然可以访问外部函数的变量
   ```javascript
     function f1(){
       var N=0;//N 是f1函数的局部变量
       function f2()
       {
          N+=1;//内部函数f2中使用了外部函数f1中的变量N
          console.log(N)   
       }
       return f2;
     }
     var result=f1();
     result(); // 输出 1
     result(); // 输出 2
     result(); // 输出 3
   ```
   代码中,外部函数f1只执行了一次，变量N设为0，并将内部函数f2赋值给了变量result。由于外部函数f1已经执行完毕，其内部变量N应该在内存中被清除，然而事实
并不是这样:我们每次调用result的时候,发现变量N一直在内存中,并且再累加，这就是闭包的神奇用处。
 ### 3.使用闭包定义私有变量
     通常，javascript开发者使用下划线作为私用变量的前缀，但是实际上这些变量依然可以被访问和修改，并非真正的私有变量。这时，使用闭包可以定义真正的私有变量
   ```javascript
    function Product(){
      var name;
      this.setName=function(value){
          name = value;
      };
      this.getName=function(){
          return name;
      };
      var p = new Product();
      p.setName('Fundebug');
      console.log(p.name); // 输出undefined
      console.log(p.getName()); // 输出Fundebug
    }
   ```
   代码中，对象p的name属性为私有变量，使用p.name不能直接访问。
