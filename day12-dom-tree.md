# dom  element tree
#### DOM API提供操作页面对象的方法   
* node type      

| n o d e           | nType | nName          | nValue            |     |     |
| ----------------- | ----- | -------------- | ----------------- | --- | --- |
| element node      | 1     | 标签大写       | null              |     |     |
| element attrib    | 2     | 属性名         | 属性值            |     |     |
| text              | 3     | #text          | 文本内容          |     |     |
| CDATA node        | 4     | #cdata-section | CDATA区域内容     | xml |     |
| 实体引用名称节点  | 5     | 引用名称       | null              | xml |     |
| 实体名称节点      | 6     | 实体名称       | null              | xml |     |
| 处理指令节点      | 7     | target         | entire content... | xml |     |
| comment node      | 8     | #comment       | comment content   |     |     |
| doc node          | 9     | #document      | null              |     |     |
| doc type node     | 10    | doctype 名称   | null              |     |     |
| doc fragment node | 11    | #doc-fragment  | null              |     |     |
| DTD声明节点       | 12    | 符号名称       | null              | xml |     |
* 属性节点包含在元素节点里面，通过dir可查看，注意textNode，被元素节点隔开的有空格的和换行的都会算一个
> \<div id="box"\>        
    nihao\<p\> \</p\>      
  \</div\>      
```javascript
let oDiv = document.getElementById("box");
console.log(oDiv.childNodes);//这个div其实有3个子节点
```
> > 文本节点创建加入到父元素里，即添加了文字，也不会像innerHTML或者innerText那样影响到兄弟元素，比如innerHTML兄弟元素的注册事件依然在,有些时候可以少创建一个页面标签等      
* 节点关系图     
 <div align="center"> ![节点关系图](https://github.com/appleu/js-Notes/blob/master/practice/images/node.png?raw=true "小肖") </div>
