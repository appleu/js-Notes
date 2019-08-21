# CSS Object Model View
######## 文档及其内容的视觉属性，包括布局框定位 根元素宽度和元素滚动         
* window.innerWidth/height 获取页面显示区的宽高，ie8不兼容         
document.documentElement \\ body \\ head \\ title           
document.documentElement.clientWidth/Height  ie8及以下         
clientWidth = width + padding   offsetWidth = width + padding + boder             
scrollWidth = 保存着实际内容宽度，包含超出的部分(不管是否设置overflow:hidden) 值number没有单位，clientWidth类似的属性可以赋值，但是没有意义， 再读时要会重新获取，scroll可以赋值并且会显现出效果      
*  offsetLeft offsetTop 获取元素到他的定位父元素的距离          
document.documentElement.scrollTop  | document.body.scrollTop -google以前用,google的chrome内核手机浏览器，很多没改过来，还是用的body.scrollTop   用兼容写法 1 || 2  
* ele.getBoundingClientRect() 返回一个DOMRect {x:50,y:60,width:10,height:10,top:20,bottom:81}           
* ele.scrollIntoView([ture|false]);让元素滚动到可视区域(h5标准),参数
* event object When the event function is executed, the first formal parameter is the event object, which stores information related to the event.
