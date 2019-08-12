# 对象遍历
< object遍历和数组不同     
```javascript
let m = {
  name:"zhangs",
  age:22,
  marry:false,
  handsome:true
};
//使用for in
for(let key in m){
  console.log(key+":"+m[key]);
}

//添加     
m.friends = ['lisi','wangwu','mazi'];     
//modify     
m.age = 33;     
//删除      
delete a.marry;      
//查找     
console.log("name" in m);//true
```

< JSON '{"name":"zhangs","age":20,"marry":"ture"}' 字符串键值对         
json里面只能是双引号，代替xml，前后台传递交换数据用
```javascript
  console.log(JSON.stringify(m));//将obj转换为json
  JSON.parse(JsonStr);//序列化    //反序列化
```
* es6 默认值
```javascript
let [a,b=10] = [5];
let [x:hh,y:tt=20] = [x:10];
function fn([a,b]){console.log(a+b)}
fn([3,2]);
fn(1);//报错，解构模式不对应

function fnn({x,y}){}
fnn({x:2,y:3});

function fnnn({x=0,y=1}){}
fnnn({});//不加{}模式不对应，会报错

function fn({x,y} ={x:1,y:3}){console.log(x +" - "+ y)}
fn();//此时不会报错
fn({});// 相当于fn({x,y} = {})   undefined - undefined
```

* arrow function
```javascript
let fn = (v) => { v };//形参只有一个可不用()
var fn = function(v){
  return v;
}

let fnn = (v) => {name:"ss",age:22};//错误，
//因为{}在arrow函数里是有多条语句执行，如果要返回对象时注意要变成下面的
let fnn = (v) => ({name:"ss",age:22});//

let f = (...b) => Math.max(...b);

let arr[3,2,1];
arr.forEach((val,ind,arr) => {
  console.log(ind +":"+val+"arr[ind]:"+arr[ind]);
})

let newArr = arr.map(v=>v*v);//新数组是原数组每个元素的平方
```

* setTimeout 定时器
< setTimeout(fn,time,param1....pn),time过后执行函数fn，p是fn的参数
fn也可以是字符串，字符串是一段某一段js代码，相当于eval功能
返回一个数字，是定时器的id(或者说编号)
clearTimeout(timeOutID);//清除定时器
```javascript
function fn(){alert(fn)}
setTimeout(fn,1000);
setTimeout("fn()",1000);//同样效果,引号执行函数，函数一定是window下的变量
setTimeout(() => {alert(1);console.log(1)},1000);
```

< setInterval(fn,time) 间隔time执行一次fn，一直执行       
clearInterval(IntervalID);//用变量接受返回的ID，然后停止     
按照出现的顺序编号，从1开始,编号连续依次累加2,3,4....(不管作用域是否相同)
```javascript
let seconds = 0;
let str ="计时："
setInterval( (str) => {console.log(`${str}${seconds}`)},1000,str);//计时：1....
```

< requestAnimationFrame(fn)，没有第二个参数，根据浏览器刷新频率自设置时间       
和setTimeout相同，由于他刷新贴合浏览器做动画比其他定时器更流畅点         
cancelAnimationFrame(ID) ，支持这个函数的浏览器一定支持css3
hack
```javascript
//hack
if(!window.requestAnimationFrame){
  window.requestAnimationFrame = function(fn){
    return setTimeout(fn,1000/60);
  }
  window.cancelAnimationFrame = function(id){  //window.cancelAnimationFrame = clearTimeout
    clearTimeout(id);
  }
}

//简写
window.requestAnimationFrame = window.requestAnimationFrame || function (f){return setTimeout(f,1000/60)};
window.cancelAnimationFrame = window.requestAnimationFrame || clearTimeout;
