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
* 实参 // 给函数内部的变量赋值
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
```
