# dom  element tree
## DOM API提供操作页面对象的方法   
* node type      
      
| n o d e           | nType | nName          | nValue            |     |
| ----------------- | ----- | -------------- | ----------------- | --- |
| element node      | 1     | 标签大写       | null              |     |
| element attrib    | 2     | 属性名         | 属性值            |     |
| text              | 3     | #text          | 文本内容          |     |
| CDATA node        | 4     | #cdata-section | CDATA区域内容     | xml |
| 实体引用名称节点  | 5     | 引用名称       | null              | xml |
| 实体名称节点      | 6     | 实体名称       | null              | xml |
| 处理指令节点      | 7     | target         | entire content... | xml |
| comment node      | 8     | #comment       | comment content   |     |
| doc node          | 9     | #document      | null              |     |
| doc type node     | 10    | doctype 名称   | null              |     |
| doc fragment node | 11    | #doc-fragment  | null              |     |
| DTD声明节点       | 12    | 符号名称       | null              |     |
