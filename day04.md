# 判断  逻辑运算  for
### 判断  三目运算  
>
>     if( condition ){
>         ...
>     }else{
>         ....
>     }
>     condition?true:false;//只比=和，的运算级高，可代替判断，需要值的地方可以放三目
>
```javascript
  <div id="wrap"></div>
  <button id="btn">控制按钮</button>
  -----
  let oWrap = document.getElementById('wrap'),
  oBtn = document.getElementById('btn'),
  bool = true;
  oBtn.onclick = function(){
    if(bool){
    oWrap.style.display = "none";
    //bool = false;
  }else{
    oWrap.style.display = "block";
  //  bool = true;
  }
  bool = !bool;
}
//以上用oWrap.style.display==="block"做条件，也可以，可以不用声明bool变量，
//注意元素的display有很多种状态，除了block还有inline-block
oWrap.style.display = oWrap.style.display === "block" ? "none" : "block";
//用三目，不用变量的话，需要给元素预先设置内联style="display:block;"否则第一次点不会隐藏
//用三目，2>5 ? ( console.log(1),console.log(2),console.log(3) ) : ( ... ); 执行多个语句用()
```
>多分支(全等)判断：switch  case  
```javascript
let condition = "垫底";
 switch(condition){
   case "满分" :
     alert("带你去旅游，吃香喝辣！");
     break;
   case "优" :
     alert("奖励书籍，并表扬。");
     break;
   case "及格" :
     alert("督促，鼓励，下次考好。");
     break;
   case "不及格" :
   case "垫底"  :
     alert("补课补课，亲自补课，给你请家教..");
     break;
   default:
     alert("还没考试吗？");
 }
```

### 逻辑运算 && || ！
> 逻辑运算符的短路运算，代替if判断
```javascript
> let a = true;
>  a && b();  //a为真b才执行，因为与运算，a为假时已经能确定逻辑运算的值
>  // 后面不会再去运算，如果a为真时才有必要去运算，确定与运算的最终值
>  a || b(); //  a为假b才执行，或运算，a为
 ```


### for

>     
>     
>     for(int i=0;i<number;i++){
>           循环体
>     }
>     //不支持markdown的流程图语法嘛，改了n次还是出不来T-T
>
```
flow
st=>start: start
e=>end
op=>operation: My operation
cond=>condition: Yes or No?
st->op->cond
cond(yes)->e
cond(no)->op
```
