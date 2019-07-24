# 函数

### 函数 函数表达式
```javascript
  let a = function b(){
    alert(1);
    console.log(b);
    console.log(b === a);//ture
  }

  a();
  b();//在外面不能使用b
> 函数表达式
  let a = function(){
    alert(2);
  }();//函数表达式可直接执行，函数声明不行

  let a = function b(){
    ...
  }();//这里不能执行

  function(){
    alert(1);
  }()//不能执行，加括号变成函数表达式

  (function(){
    alert(1);
  })();//可以执行
  //或者
  (function(){
    alert(1);
  })
  +functoin(){
    alert(1);
  }();//在函数前加 +  -  ~ ! 这几个符号可以把一个函数声明变成表达式，后面加括号可以执行

```
### 参数
* 形参  //相当于是函数内部的变量
* 实参 // 给函数内部的变量赋值，此值没有数据类型限制，*可以是基础类型和，甚至可以是函数*
* 不定参
> // 如果实参少于形参，相当于函数内部的变量没有赋值是undefined
> 实参多于形参，js函数不会报错，获取多出来的实参，可通过arguments(存储所有实参的类数组)
```javascript
  //求不确定个数参数之和的函数
  function sum(){
   let sumNum = 0 ;
   for(let i = 0,len = arguments.length; i < len ; i++){
    sumNum += arguments[i];
 }
 return sumNum;
}

function a(){
  a();
}
a();//报错 : Maximum call stack size，无限递归肯定是不能被允许
//求阶乘用递归
```
### this
```javascript
alert(a);//会报错 not defined
if(requestAnimationFrame);//也一样
if(window.requestAnimationFrame);//不会出错

let a = function(){
 console.log(this);
}
console.log(a === window.a); //false ,如果用var声明a，则是true
//无论是let声明还是var声明，直接声明的函数自执行的话他的this都指向window
let f ={
  name:"aaa",
  x:function(){
  console.log(this);
}
}
f.x();//对象方法自执行，this指向对象，对于对象里的对象的方法，指向是方法的直接对象
```

### return
> 每个函数都有返回值，不写return默认返回undefined，js可返回任何数据类型,可返回函数

### 作用域
> es5 和 es6
```javascript
var a = 3;
if(a<2){
 var b = 4;
}
console.log(b);//es5 : undefined   (有点不合符逻辑，怪异)

if(a<2){
  let b = 4;
}
console.log(b);//es6 : not defined 报错 (es6比es5看起来符合逻辑一点)
//es6的let让js有块作用域


```
