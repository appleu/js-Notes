### string    array
* 包装对象
```javascript
let str = "aaa";
str.index = 3;
console.log(str.index);//undefined
// 包装过后变成对象，可以添加属性保存值
let str1 = new String("aaa");
str1.index = 3;
console.log(str1);// 3
```
* charCodeAt 得到某一个字符的ASCII码  fromCharCode 把ASSCII码转化成字符
```javascript
let str ="ABC";
console.log(a.charCodeAt(0));//65
console.log(String.fromCharCode(65));//A
```
* API
```javascript
let str2 = "fse五fs三五fSef";
let subs = str2.substring(6,8);//截取子字符串,(5,8]，一个参数从当前位置到末尾
let subss = str2.substring(8,6);//顺序换掉也没问题
console.log(subs);//三五
console.log(subss);//三五

let subs2 = str2.substring(-2,3);//负数被认为是0，
let subs3 = str2.slice(-5,-2);//倒数第5个到倒数第2个，5fs,参数顺序不能换

sub3.toUpperCase();//sub3.toLocaleUpperCase();
sub3.toLocaleLowerCase();

//indexOf  查找
let ss = str2.indexOf("五");//查找到就会暂停，第二个参数可指定查找的起始位置
console.log(ss);//3 如果查找的字符不存在返回-1

//split
let str333 = "诸葛亮,赵子龙,刘备,关羽,张飞,吕布,貂蝉,马超,许诸"
let strArr = str333.split(",");//以逗号切割，这里也可以写正则表达式
console.log(strArr);// 变成一个人名数组
//字符串的操作用的最多的是正则表达式，匹配字符串
```

### array
* push，改变原数组，向数组后面添加数据
> 多个参数添加多个数据，arr.push(parameter1....2...parametern),返回数组长度

* pop，改变原数组，删除数组最后一个元素，不接受参数
> arr.pop();返回删除的元素
```javascript
let arr = [77,function(val){alert(val)}];
arr.pop()(arr[0]);//输出？
```

* shift 从最面开始删除  unshift 从前面开始添加
> 很多字符串的方法可用于数组，比如indexOf和slice，数组方法不可用于类数组

* splice()
> 切除数组里的元素，可以有两个参数，(star,num,val1,val2...valn)从s开始切除num位,

> 后面的参数是替换数据，num为0，就是添加数据进数组的指定位置
* sort() 指定参数，排序方式 -> function(x,y){ return x - y; }
> 改变数组，默认从小到大排序 ，升序，返回值是排好序的数组，所以可以：a.sort().reverse();

* reverse()
> 反序，把数组反过来,返回数组

### es6 相关
* 模板字符串，可代替()来向函数传递参数
```javascript
  function fn(){

  }
  let a = 6;
  fn`stra${a+1}b${a+2}c`; // 等价于下面
  fn(["stra","b","c"],7,8);
```

* 检测包含关系
> str.includes(substr);// true or false  

> str.includes(substr,start);// 指定开始位置  

> str.[start|end]Width(substr[,start]);//是否在原字符串的[头部|尾部]，可指定开始位置  

> str.rpeat(num);//返回新字符串，将原字符串重复num次；num负报错，有小数位舍弃，其他能转则转  

> "xx".padStart(2,"a"); // => "aaxx";  

> "xx".padEnd(2,"a");// => "xxaa";  

> 常用于时间，数位补全 (5+"").padStart(2,"0");//05  

> 年月日格式 “05-30”.padStart(10,"YYYY-MM-DD");//"YYYY-05-30"  
