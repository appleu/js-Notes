# js的数据类型
### 原始数据类型
* Number
< *NaN一个特殊的Number,一个不是数字的数字类型T-T*
* String
* Boolean
| 能被      | 转为 | false | 的  | 值  |
| --------- | ---- | ----- | --- | --- |
| undefined | null | 0     | ''  | NaN    |
* undefined 用来存原始数据，暂时没赋值
* null 空指针，用来存对象的，只是暂时没有数据，typeof时是对象类型，但是他不是对象是null类型
* Symbol ->es6   babeljs.cn （es6 => es5）

### 引用类型 object   typeof(date) 检测数据类型
* array 数组
* 自定义对象 var a = { }
* 系统内置对象
  > document 可以用console.dir(document)查看document对象所有的属性
  > 系统内置对象非常多，window  console...
* 函数 function  1主动自执行  2作为事件函数触发被动执行  

### 赋值关键字
* var
* const 常量，声明时就必须赋值
* let es6新语法

### [] && .
* 数组取值 arr[index],不止数组可以这样取值，当用"."去取某一个对象的属性时，我们可以用[]来代替.
>
  ```javascript
    var a ={name:"xiao",age:20};
    var x = "name" ;
    console.log(a[x]+":"+a["age"]) //
    console["log"](a[x]+":"+a["age"]) // 都会输出 => xiao：20
  ```
