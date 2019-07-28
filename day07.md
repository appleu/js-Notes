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
