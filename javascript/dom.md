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

* Ex1

````
var win = window.open('https://baidu.com', 'yxqWin', 'height=400,width=400,top=10,left=10,resizable=yes');
win.opener = null;
````

* Ex2

````
function clickMe() {
    //本页面打开
    //location.assign('https://www.baidu.com');
    //新打开窗口
    open('https://www.baidu.com');
}

<button onclick="clickMe();">Click Me</button>
<!-- 新打开窗口 -->
<form action="https://www.baidu.com" target="_blank">
    <input type="submit" value="submit"/>
</form>
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

