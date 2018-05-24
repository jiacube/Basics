### nodeType nodeName
*nodeType*：nodeType属性返回以数字值返回指定节点的节点类型。

* 如果节点是元素节点，则nodeType属性返回1。
* 如果节点是属性节点，则nodeType属性返回2。

*nodeName*：nodeName属性可依据节点的类型返回其名称。
* 如果节点是一个元素节点，nodeName属性将返回标签名。
* 如果节点是一个属性节点，nodeName属性将返回属性名。
* 其他节点类型，nodeName属性将根据不同的节点类型返回不同的节点名称。

### 特性(Attribute) 属性(Property)
**attribute**是**HTML**标签上的特性[DOM标签中出现的属性(HTML代码)]，它的值只能够是**字符串**。但是有些常用特性(id、class、title等)会被转化为Property。

**property**是DOM中的属性，是**JavaScript**里的对象。用.获取的是style属性Property，可以给属性Property赋**任何类型的值**。

### BOM
* window
浏览器的一个实例
* location
* navigator
* screen
* history


