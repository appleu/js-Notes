# scope | closure | this指向

### scope
* script标签是最大的作用域，称之为全局作用域
> 如果var、function在全局作用域下定义了变量，相当于给window添加属性
  ```javascript
    funciotn foo(){
      var x = y = 5;//不推荐此写法
  }
  foo();
  console.log(y);//  5  y 没有加var声明，不在strick模式下会在全局作用域下创建变量y
  // console.log(y === window.y)// true
  console.log(x);//error： x is not defined
  ```
* var  function 在最近的包含自己的函数中
> 在函数中定义变量，就是局部作用域变量

### closure
* js自动垃圾回收机制
  > 当变量不会发生调用时回收，全局变量不会回收，直到页面关闭，所以尽量避免全局变量

* 一个使用了外部函数的参数或者变量的函数
```javascript
function foo(){
  var x = 0;
  function b(){  //closure
    var y = 1;
    x++;
    y++;
    console.log(x + ":"+ y);
  }
  return b;
}
var innerFunction = foo();// closure 对外部变量引用的一个内部函数赋值给了innerFunction
innerFunction();//1:2  y值不会随着执行次数累加，y是自身内部变量，每次执行函数，每次开始y = 1
innerFunction();//2:2
innerFunction();//3:2; foo的x不会回收，因为innerFunction变量引用了foo的内部函数，
//内部函数引用了foo的变量x,每次执行innerFunction都会引用同一个foo中的x,

foo()();// 1:2
foo()();// 1:2
foo()();// 1:2 每次执行都是新的作用域，每次var x = 0,就是父级不同，每次返回函数对 x++
```
* es6 scope 嵌套就会产生闭包
```javascript
  let aP = document.querySelectorAll('#info p');
  for(let i = 0 , len = aP.length ; i < len ; i++){
    aP[i].onclick = function(){
      //每次循环产生一个闭包，会产生5个不同的i，在各自作用域中，es5不行
      alert(i);
    }
  }

  // es5 的做法其实就是借助函数产生新作用域
  let aP = document.querySelectorAll('#info p');
  for(let i = 0 , len = aP.length ; i < len ; i++){
    function foo(i){
      aP[i].onclick = function(){
      alert(i);
      }
    }
    foo(i); // 执行函数，aP[i]绑定的事件函数引用了外部变量i，形成闭包      
    //综合写成匿名函数自执行  上面代码可换成自执行
    ~function(i){
      aP[i].onclick = function(){
      alert(i);
    }(i)
  }

  //下面函数执行结果 undefined 11  
  foo1()();
  var a = 9;
  function foo1({
      console.log(a);
      var a = 10;
      function f(){
      a++;
      console.log(a);
      }
      return f;
  }

  //想想下段代码运行结果
  var variableA = 5;
  function foo2(){
    var variableA = 10;
    console.log(variableA);
    function innerF(){
      variableA++;
      console.log(variableA);
    }
    return innerF;
  }

  var functionA = foo2();
  functionA();
  foo2()();
  functionA();
//
console.log(5 === 5);//true
console.log([] === []);//false

var functionAA = function(){};
var functionBB = function(){};
console.log(functonAA === functionBB);//false

function Fcc(){
  return function(){};
}
var dd = Fcc();
var ee = Fcc();
console.log(dd === ee);//false
```

### ES6中默认严格模式strick

### ES6 let const function class
* let 的声明不会提前，var声明提前，赋值在原位置
```javascript
console.log(bb);//error : bb is not defined
let bb = 10;
console.log(bb1);//undefined
var bb1 = 12;

let bb3 = 20;
function functionB(){
  alert(bb3);//error:bb3 is not defined暂时性死区，只要在作用域中let过变量，那就不允许提前使用，即使父级作用域中有
  let bb3 = 30;//如果这里没有let关键字，没有暂时性死区，那么弹出20
}

{
  let bbb = 220;//产生作用域
}

//var只认函数作用域,所以
if(false){
  var bbbb = 22;
}
alert(bbbb);//并不会报错，undefined

//const  常量，声明时必须赋值，并且不能重新赋值，但是如果是数组，注意有点特殊
const ccc = [];
ccc[0] = 10;
ccc[0] = "hello world";
ccc[1] = "hey honey！！"
console.log(ccc); //是可以添加，修改的
```
### this指向 call  apply  bind
* 宽松模式下，this指向window，绑定的事件函数指向触发事件的对象
```script
function foo(x,y){
  console.log(x+"  :  "+y);
  console.log(this);
}
foo("函数自执行",3);//函数自执行 : 3 #window
foo.call(document,"nihao",6);
foo.apply(document,["nihao",6])
//nihao : 6 #document  call(parament1,parament2....n) parament1改变this指向
//apply(parament1,[parament2....n])
foo.bind(document);//改变this指向，但是不会立刻执行
foo.bind(document,10,100)();//10 : 100 document,bind返回函数
```
*
