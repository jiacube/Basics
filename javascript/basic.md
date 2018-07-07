### this

#### this是调用函数的那个对象

* 当在函数调用的时候指向window

* 当方法调用的时候指向调用对象

* 当用apply和call上下文调用的时候指向传入的第一个参数

* 构造函数调用指向实例对象

#### 箭头函数的this对象就是定义时所在的对象，而不是使用时所在的对象。

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

#### cookie、sessionStorage、localStorage、indexedDB

##### 相同点

都保存在浏览器端，同源

##### 不同点

* 传递方式不同

cookie会在浏览器和服务器间来回传递

sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存

* 存储数据大小不同

cookie数据大小不能超过4k

sessionStorage虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大

* 数据有效期不同

localStorage存储持久数据，浏览器关闭后数据不丢失除非主动删除数据

sessionStorage数据在当前浏览器窗口关闭后自动删除

cookie设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭

* 作用域不同

#### Session和Cookie的区别

session是服务器端保存的一个数据结构，用来跟踪用户的状态，这个数据可以保存在集群、数据库和文件中。

Cookie是客户端保存用户信息的一种机制，用来记录用户的一些信息。

session的运行依赖于session ID, session ID是存在于Cookie中。

### 跨域

同源策略是浏览器的一个安全功能，不同源的客户端脚本在没有明确授权的情况下，不能读写对方资源。

若地址里面的协议、域名和端口号都相同则属于同源。

#### 跨域处理方式

1. Ngnix反向代理

2. Node.js中间件代理跨域

3. 跨域资源共享CORS

浏览器和服务器端通过头部信息来进行沟通确认是否给予响应。

* 简单请求 Access-Control-开头

Access-Control-Allow-Origin

Access-Control-Allow-Credentials: Bool值，是否允许发送Cookie

Access-Controll-Allow-Methods

* 非简单请求 [预检请求]

4. JSONP

利用script标签中src属性的链接可以访问跨域的js脚本。服务器不再返回JSON格式的数据，而是返回一段调用某个函数的js代码，在src中进行调用。

````
//JS代码
function handle(dataFromServer) {
    console.log(dataFromServer);
}

//服务器返回的内容
handle({'name': 'YXQ'});
````

5. window.postMessage

window.open() | iframe

HTML5提供了在网页文档之间相互接收与发送信息的功能。

获取到网页所在窗口对象的实例

````
//otherWindow始终是你要通信的目标页面的window
otherWindow.postMessage(message, targetOrigin, [transfer]);
window.addEventListener('message', function(e){
    /*
        source:消息源，消息的发送窗口
        origin:消息源的URI(可能包含协议、域名和端口)，用来验证数据源
        data:发送方发送给接送方的数据
    */
}, false);
//window.attachEvent('message', function(e){})
````

6. domain.name 子域

### 声明提升(变量|函数)

````
function a(){}
var a;
console.log(typeof a); //function
````

````
console.log(a); //undefined
var a = 1;
var getNum = function() {
    a = 2;
}
function getNum() {
    a = 3;
}
console.log(a); //1
getNum();
console.log(a); //2
````

### 函数节流(throttle) | 函数去抖(debounce)

#### 适应场景

* 频繁执行DOM操作、资源加载等行为，导致UI停顿甚至浏览器崩溃

* window对象的resize、scroll事件

* 拖拽时的mousemove事件

* 射击游戏中的mousedown、keydown事件

* 文字输入、自动完成的keyup事件

#### debounce函数去抖

手指一直按住一个弹簧，它将不会弹起直到你松手为止。

调用动作n毫秒后，才会执行该动作，若在这n毫秒内又调用此动作则将重新计算执行时间。

````
var debounce = function(time, fn) {
    var timeoutID;
    return function() {
        var that = this, args = arguments;
        clearTimeout(timeoutID);

        timeoutID = setTimeout(function(){
            fn.apply(that, args);
        }, time);
    }
}
````

#### throttle函数节流

水龙头拧紧直到水是以水滴的形式流出，那你会发现每隔一段时间，就会有一滴水流出。

预先设定一个执行周期，当调用动作的时刻大于等于执行周期则执行该动作，然后进入下一个新周期。

````
var throttle = function(time, fn) {
    var lastTime = 0;
    return function() {
        var curTime = +new Date();//+new Date <=> (new Date()).getTime()
        if (lastTime - curTime > time) {
            fn.apply(this, arguments);
            lastTime = curTime;
        }
    }
}
````

### 闭包

#### 定义

闭包是指有权访问另一个函数作用域中的变量的函数。-《JavaScript高级程序设计》

从技术的角度讲，所有的JavaScript函数都是闭包；它们都是对象，它们都关联到作用域链。-《JavaScript权威指南》

当函数可以记住并访问所在的词法作用域时，就产生了闭包，即使函数是在当前词法作用域之外执行。-《你不知道的JavaScript》

#### 作用

读取函数内部的变量

让这些变量始终在内存中

#### Ex

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

### SVG和Canvas的区别

#### SVG

不依赖分辨率

支持事件绑定

大型渲染区域的程序(例如百度地图)

不能用来实现网页游戏

#### Canvas

依赖分辨率

不支持事件绑定

最合适网页游戏

### JavaScript异步编程

回调函数   事件监听   发布/订阅   Promise对象

#### Promise

````
const sleep = (time) => new Promise((resolve, reject) => setTimeout(resolve, time));
(async function(){
    for (var i = 0; i < 5; i++) {
        await sleep(1000);
        console.log(i);
    }
})();
````

#### Generator

1. Generator的实现方式

````
function createIterator(items) {
    var i = 0;
    return {
        next: function() {
            var done = (i >= items.length),
                value = done ? undefined : items[i++];
            return {
                done: done,
                value: value
            };
        }
    };
}
````

2. 创建generator函数的方式

* 函数声明

````
function* createIterator() {
    yield 1;
    yield 2;
    return 3;
}
````

* 函数声明

````
function* createIterator() {
    yield 1;
    yield 2;
    return 3;
}
````

* 对象简写

````
let o = {
    *createIterator(items) {
        yield 1;
        yield 2;
        return 3;
    }
};
````

#### Async

````
function timeout(ms) {
    return new Promise((resolve) => {
        setTimeout(resolve, ms);
    });
}

async function asyncPrint(value, ms) {
    await timeout(ms);
    console.log(value);
}

asyncPrint('Hello World!', 50);
````

### Ajax

* readystate

0: (未初始化)未调用open方法

1: (载入)已调用send方法，正在发送请求

2: (载入完成)send完成

3: (解析)正在解析响应内容

4: (完成)响应内容解析完成

### 图片处理

#### 图片预加载

* 原理

通过CSS或者JavaScript，先请求图片到本地，再利用浏览器的缓存机制，当要使用图片时(图片路径一致)，浏览器直接从本地缓存获取到图片，加快图片的加载速度。

#### 图片懒加载

