# day02 js书写位置 getElement 常用方法

### javascript可以写在哪里
* head body的任何位置，不太复杂的页面，推荐写在body结束标签之前
 ```html
  <html>
    <head></head>
    <body>
      ...
      <script>
        js code
      </script>
    </body>
  </html>
  ```
* 写在单独的js文件里，通过标签<script src="path/fileName.js" ></script>来引用
* 行内js代码，不推荐，测试临时用下可以
  ```HTML
    <div id="wrap" onclick="alert(111)"></div>

    <a href="javascript:;"></a>       
    <a href="javascript:void(0);"></a>   a标签不跳转
    ```
### 操作元素属性 、 样式
< js操作css
>     内部样式表
>     行内样式

```javascript
//操作内部样式表
let oStyle = document.getElementById('css');
oStyle.innerHTML = "#wrap{width:200px;height:60px;background-color:#f36;}";

//或者,style里添加需要的类名样式，给获取的元素添加相关的className，修改的样式比较多时推荐
let oDiv = document.getElementById('wrap');
oDiv.className = "info-div";  // class 是保留字，所有用className就是操作元素的class属性

//操作(读写)合法的标签属性
oDiv.title = "infomation"; // 类似的合法属性 比如 id class style
console.log(oDiv.title);
oDiv.style = "width:300px;height:100px;";
// style是个对象，用+=并不能合并之前行内存在的style，可用style.cssText
//style对象存储关于节点的所有行内(内联)样式，并不包含内部和外部样式

oDiv.id = "modified";//虽然修改了id，但是通过id获取的元素只会获取一次，后面用oDiv还是代表原来的
od = document.getElementsByClassName('info');
		od[0].className = "info1";
		//odiv.id = "goudan";
		//odiv.innerHTML = "123";
		od[0].innerHTML = "345";//但是这里却修改不了，因为className会重新获取，
```

> 操作自定义属性,vue和bootstrap都是基于自定义属性做dom操作的
        > ele.getAttribute()
        > ele.setAttrbute（'',''） //可设置，也可添加
        > ele.removeAtrribute()
