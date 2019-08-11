# ES6相关
* 类数组不能调用数组的forEach，
```JavaScript
let aP = document.getElementByTagName('p');
aP.forEach();//会报错
//es5解决
let arr = [].slice.call(aP);//切割的数组的时候把调用方法的对象通过call换成了类数组
arr.forEach(function(node,index){
  node.onclick = function(){
    alert(index);
  }
})
//少用一个变量
[].slice.call(aP).forEach(function(node,index,arr){...})

//es6 使用...简单
[...aP].forEach(function(n,i,a){...})

function fn(a,...b){  //形参也可以使用...,但是。。。只能放到最后一个参数
  console.log(a);
  console.log(b);
}
fn(1,2,7);//1 [2,7]
function f(...rest){ }//rest数组接受所有实参，和类数组arguments不同rest是一个数组

let [a,...b] = [3,2,5];//相当于es5严格模式下 var a = 3，b=[2,5]

```

* Math对象
> Math.PI    
> Math.pow(2,3)//8    
>如果一个数开3次方，根号3里面放个8，求8的开3次方，可以用Math.pow(8,1/3);    
>Math.sqrt(4)//只能开平方，但是pow可以开任意次方，所以sqrt可废弃不用pow(4,.5)
>Math.floor(2.5);//向下取整是2
Math.floor(-2.5);//-3
>Math.cell(2.5);//向上取整3
Math.cell(-2.5)//-2
Math.round(2.49)//四舍五入取整，2
Math.trunc(2.1415926);//删除小数部分

* 三角函数
>圆一周的角度是360deg  已知角度求弧度    
Math.PI*2 = 360deg     
Math.PI/6 = 30deg     
Math.PI/3 = 60deg
sin 对边/斜边    
cos 邻边/斜边
tan 正切 对边/邻边     
Math.asin();//反正弦，已知比值求      
Math.random();//随机数  1 > num > 0     
//大于n小于m的随机数    (m-n) 乘以 Math.random() + n;     
const rdm = (n,m)=>(m - n)\*Math.ruandom()+n; // 注意取值区间[n,m)     
//彩票系统 一等奖2%  二等奖10% 三等奖30%  谢谢参入     
parseInt  parseFloat  不是数学对象，是window下的方法       
parseInt(“123abc”);//返回字符串的整数部分，碰到非数字字符停止     
parseInt(a,b);//a是需要转换的变量   b是进制(2,8,10,16,   其实可以36)
parseInt("zz",36);//1295  (数值 0-9 a-z  10个数字+26个字母，36)     
进制的转换，如把10进制转换成2进制，怎么做     
parseInt 和 parseFloat 先把传入的转换参数调用toString(),然后再转换，怎么验证
let obj = {     
  toString(){     
  return 123;     
 }     
}     
parseInt(obj)// 123     
mdn Math     
https://cloudconvert.com/gif-to-mp4
