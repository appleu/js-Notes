# js运动
> css3运动要确定动画时间，假如只有速度，不要确定时间就需要用js来做
```javascript
let dom = document.querySelector("xx");
let s = s1 = 0;
function fn(){
  dom.style["marginLeft"] = ++s+"px";
  setTimeout(fn,500);
}
fn();
//或者
function fn1(){
  dom.style["width"] = ++s1+"px";
}
setInterval(fn1,100);
//当fn里面有比较复杂的运算时，用setTimeout会比setInterval好，setInterval不管函数有没执行
//完，都会在第2个参数规定的时间内第二次调用执行函数，会导致有可能第一次还没执行完


//单独的js文件
/*
** 元素的动态改变的封装
**  parameter
**			dom 要改变的dom元素
**			attr  要改变的元素属性
**			target  变化的最终值
**			step  变化的步长
*/

function move(dom,attr,target,step){
	var cssObj = window.getComputedStyle ? getComputedStyle(dom) : currentStyle(dom);
	//var requestAnimationFrame = window.requestAnimationFrame ? requestAnimationFrame : setTimeout;
	var requestAnimationFrame = window.requestAnimationFrame ||  setTimeout.bind(null,fn,1000/65);;
	var sVal = parseFloat(cssObj[attr]);

	function fn(){
		if(sVal >= target){
			dom.style[attr] = target +"px";
		}else{
			sVal += step;
			dom.style[attr] = sVal + "px";
			requestAnimationFrame(fn);
		}
	}

	fn();
}


/////////////////////////////////////////////////////////////////////////////////////////////////////////

window.move = (function(){
	var requestAnimationFrame = window.requestAnimationFrame ? window.requestAnimationFrame : function(f){ setTimeout(f,1000/60)};
	var cancelAnimationFrame = window.cancleAnimationFrame || clearTimeout ; // iehack >= ie9
	//由于要把上面的兼容代码只要执行一次，从定时器中分离出来，封装的更好看点，把move改成一个自执行函数，我们返回一个函数
	//return function(dom,attr,target,step=5){ //默认步长参数，新写法，不兼容ie
	return function(dom,attr,target,step){//兼容ie就写到函数里去吧默认参数，这里不加
    step = step || 6;
		var cssObj = window.getComputedStyle ? getComputedStyle(dom) : dom.currentStyle;
		var sVal = parseFloat(cssObj[attr]);
		function fn(){//if - else 改写成一条，看起来有点长
			sVal >= target  ? dom.style[attr]=target+"px" :  ( dom.style[attr]=(sVal+=step)+"px",requestAnimationFrame(fn) );
		}
		fn();
	}
})()

//当初始值 大于 target ，当attr为opacity时的兼容问题等等
//小测试  商品按照价格排序    随机色卡   圆周运动  
//BFC   浮动后 高度坍塌  父元素overflow:hidden;
