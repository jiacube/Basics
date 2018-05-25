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

    top parent self

    窗口位置
````
//screenX->Firefox
var leftPos = (typeof window.screenLeft == 'number') ? window.screenLeft : window.screenX,
topPos = (typeof window.screenTop == 'number') ? window.screenTop : window.screenY;
````
窗口大小
````
var pageWidth = window.innerWidth,
    pageHeight = window.innerHeight;
if (typeof pageWidth != 'number') {
    if (document.compatMode == 'CSS1Compat') {
        pageWidth = document.documentElement.clientWidth;
        pageHeight = document.documentElement.clientHeight;
    } else {
        //IE6 混杂模式
        pageWidth = document.body.clientWidth;
        pageHeight = document.body.clientHeight;
    }
}
````
打开窗口
````
var win = window.open('https://baidu.com', 'yxqWin', 'height=400,width=400,top=10,left=10,resizable=yes');
win.opener = null;
````
* location

网址：location.href

协议：location.protocol

path：location.pathname

参数：location.search

hash：location.hash

* navigator

获取浏览器特 navigator.userAgent
* screen

屏幕的宽度：screen.width

屏幕的高度：screen.height
* history
````
//后退一页
history.back();
//前进一页
history.forward();
//前进两页
history.go(2);
````
### 事件
事件流描述的是从页面中接收事件的顺序。

*事件冒泡(event bubbling)*[IE]：事件开始时由最具体的元素(文档中嵌套层次最深的那个节点)接收，然后逐级向上传播到较为不具体的节点(文档)。

*事件捕获(event capturing)*：不太具体的节点应该更早接收到事件，而最具体的节点应该最后接收到事件。

DOM事件流的三个阶段：*事件捕获阶段*、*处于目标阶段*、*事件冒泡阶段*
