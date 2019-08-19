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
  ![节点关系图](https://github.com/appleu/js-Notes/blob/master/practice/images/node.png?raw=true "小肖")
* 常用方法       
> elementNode nodeValue是为null，而不是中间的文字或者包含的标签，input的value也不是input标签的nodeValue，二是eleAttribute value的NnodeValue,
textNode的nodeValue就是文本内容 。       
childNodes 一级子节点集合  children 一级子元素 ，获取一个元素下所有子节点需要自己写递归函数              
> 增            
> > 1 sonNode = document.createElement("p")/createTextNode("hello")/createComment("")                 
    2 parentNode.appendChild(sonNode)     parentNode.insertBefore(sonNode,targetele)//目标子节点之前,如果父元素没有子节点目标节点undefined也可以      
    > 删         
    > > 1 sonNode = document.querySelector 获取要删除的节点  parent = sonNode.parentNode 获取父节点                 
        2 parent.remove(sonNode);//删除之后还可以再添加到其他地方，因为此时节点的变量还保存在内存中  otherEle.appendChild(sonNode)           

        ```javascript
        son1 = parent1.child;
        son2 = parent2.child;
        parent1.appendChild(son2);
        parent2.appendChild(son1);
        //节点的唯一性，从父节点消失，出现在另外一个地方，交换位置，事件不收影响，但css的话可能会有所改变          
        ```          
> getAttributeNode 获取指定属性节点          
document.createAtrribute('aName') 创建指定名称属性节点      
setAttributeNode 向元素中添加属性节点        
> firstChild / firstElementChild 第一个子节点        
ele.firstChild 只读属性，标准下会包含文本节点，非标准下只包含元素节点              
ele.firstElementChild 只读属性，标准下获取第一个元素类型节点，非标准下无           
lastChild / lastElementChild  nextSibling / nexElementSibling  previousSibling ...兼容性同上              
parentNode / offsetParent(最近定位)    childElementCount 子节点数量 
