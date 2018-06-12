### this

* 当在函数调用的时候指向window

* 当方法调用的时候指向调用对象

* 当用apply和call上下文调用的时候指向传入的第一个参数

* 构造函数调用指向实例对象

### call、apply和bind

改变某个函数运行时的上下文(context)，即改变函数体内部this的指向。

第一个参数都是this要指向的对象，即指定的上下文；利用后续参数传参。

bind返回绑定函数，便于稍后调用；call、apply是立即调用。

call和apply作用完全一样，接受参数方式的方式不一样。

````
//this是指定的上下文，call把函数顺序传递进去，apply是把参数放在数组里进行传递。
func.call(this, arg1, arg2);
func.apply(this, [arg1, arg2]);
````

### 存储方式

cookie、sessionStorage、localStorage、indexedDB

**相同点**：都保存在浏览器端，同源

**不同点**：

* 传递方式不同

* 数据大小不同

* 数据有效期不同

* 作用域不同

#### Session和Cookie的区别

session是服务器端保存的一个数据结构，用来跟踪用户的状态，这个数据可以保存在集群、数据库和文件中。

Cookie是客户端保存用户信息的一种机制，用来记录用户的一些信息。

session的运行依赖于session ID, session ID是存在于Cookie中。

### 跨域

同源策略是浏览器的一个安全功能，不同源的客户端脚本在没有明确授权的情况下，不能读写对方资源。

若地址里面的协议、域名和端口号都相同则属于同源。

**跨域处理方式**：

* JSONP

* 跨域资源共享CORS   Access-Control-Allow-Origin: *

* Ngnix反向代理

* Node.js中间件代理跨域

### 事件循环(Event Loop)

执行栈 事件队列(Task Queue)

宏任务：setInterval()   setTimeout()

微任务：new Promise()   new MutaionObsever()

当前的执行栈执行完毕时会立刻先处理所有微任务队列中的事件，
然后再去宏任务队列中取出一个事件，同一个事件循环中，
微任务永远在宏任务之前执行。

### 声明提升(变量|函数)

### 闭包

### 原型及原型链

* 原型

所有的引用类型(数组、对象、函数)，都具有对象特性，即可自由扩展属性(null除外)。
所有的引用类型(数组、对象、函数)，都有一个__proto__属性，属性值是一个普通的对象。
所有的函数，都有一个prototype属性，属性值是一个普通的对象。
所有的引用类型(数组、对象、函数)，__proto__属性值指向它的构造函数的prototype属性值。

* 原型链

链式结构

### 重绘和回流
*重绘*：当页面中元素样式的改变并不影响它在文档流中的位置时(EX:color|visibility)，浏览器会将新样式赋予给元素并重新绘制它。
*回流*:当Render Tree(DOM)中部分或全部元素的尺寸、结构或某些属性发生改变时，浏览器重新渲染部分或全部文档的过程。
回流要比重绘消耗性能开支更大。
回流必将引起重绘，重绘不一定引起回流。

### 函数节流(throttle) | 函数去抖(debounce)

* 频繁执行DOM操作、资源加载等行为，导致UI停顿甚至浏览器崩溃

1.window对象的resize、scroll事件

2.拖拽时的mousemove事件

3.射击游戏中的mousedown、keydown事件

4.文字输入、自动完成的keyup事件

* debounce函数去抖

调用动作n毫秒后，才会执行该动作，若在这n毫秒内又调用此动作则将重新计算执行时间。

* throttle函数节流

预先设定一个执行周期，当调用动作的时刻大于等于执行周期则执行该动作，然后进入下一个新周期。

### 变量提升

````
function a(){}
var a;
console.log(typeof a); //function
````

### 闭包

* 定义

1. 闭包是指有权访问另一个函数作用域中的变量的函数。-《JavaScript高级程序设计》

2. 从技术的角度讲，所有的JavaScript函数都是闭包；它们都是对象，它们都关联到作用域链。-《JavaScript权威指南》

3. 当函数可以记住并访问所在的词法作用域时，就产生了闭包，即使函数是在当前词法作用域之外执行。

* Code Example
````
var scope = "global scope";
function checkScope() {
    var scope = "local scope";
    function f() { return scope; }
    return f();
}
checkScope();//local scope

var scope = "global scope";
function checkScope() {
    var scope = "local scope";
    function f() { return scope; }
    return f;
}
checkScope()();//local scope
````

### 物理分辨率 逻辑分辨率

物理分辨率是硬件所支持的，逻辑分辨率是软件可以达到的，互转的话乘以像素倍率。

### 从服务器主动推送data到客户端的方式

html5 websoket | WebSocket通过Flash | XHR长时间连接 | XHR Multipart Streaming | 不可见的iframe

### SVG和Canvas的区别

* SVG

不依赖分辨率

支持事件绑定

大型渲染区域的程序(例如百度地图)

不能用来实现网页游戏

* Canvas

依赖分辨率

不支持事件绑定

最合适网页游戏