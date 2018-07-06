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

### 从服务器主动推送data到客户端的方式

#### WebSocket

WebSocket协议本质上是一个基于TCP的协议，在单个TCP连接上进行全双工通讯。

为了建立一个WebSocket连接，客户端浏览器首先要向服务器发起HTTP请求，这个请求和通常的HTTP请求不同，包含了一些附加头信息，其中附加头信息"Upgrade: WebSocket"表明这是一个申请协议升级的HTTP请求，服务器端解析这些附加的头信息然后产生应答信息返回给客户端，客户端和服务器段的WebSocket连接就建立起来了，双方就可以通过这个连接通道自由地传递信息，并且这个连接会持续存在直到客户端或者服务器端的某一方主动地关闭连接。

* WebSocket属性

只读属性readyState表示连接状态

0: 表示连接尚未建立。

1: 表示连接已建立，可以进行通信。

2: 表示连接正在进行关闭。

3: 表示连接已经关闭或者连接不能打开。

只读属性bufferedAmount已被send()放入正在队列中等待传输，但是还没有发出的UTF-8文本字节数。

````
function testWebSocket() {
    if ('WebSocket' in window) {
        //创建WebSocket对象
        var ws = new WebSocket(url, [protocol]);
        
        //连接建立时触发
        ws.open = function() {
            //使用连接发送数据
            ws.send();
        }

        //客户端接收服务端数据时触发
        ws.onmessage = function(evt) {
            console.log('接收的数据', evt.data);
        }

        //通信发生错误时触发
        ws.error = function() {
            //关闭连接
            ws.close();
        }

        //连接关闭时触发
        ws.close = function() {

        }
    } else {
        console.log('Brower cann't support WebSockt.');
    }
}
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

#2018-07-06 补充
##日期

###日期常规操作
```python
var myDate = new Date();            //获取当前日期时间

myDate.getYear();                  //获取当前年份(2位)

myDate.getFullYear();              //获取完整的年份(4位,1970-????)

myDate.getMonth();                 //获取当前月份(0-11,0代表1月)

myDate.getDate();                  //获取当前日(1-31)

myDate.getDay();                   //获取当前星期X(0-6,0代表星期天)

myDate.getTime();                  //获取当前时间(从1970.1.1开始的毫秒数)

myDate.getHours();                //获取当前小时数(0-23)

myDate.getMinutes();              //获取当前分钟数(0-59)

myDate.getSeconds();              //获取当前秒数(0-59)

myDate.getMilliseconds();         //获取当前毫秒数(0-999)

myDate.toLocaleDateString();      //获取当前日期

var mytime=myDate.toLocaleTimeString();     //获取当前时间

myDate.toLocaleString( );        //获取日期与时间
```

###日期时间脚本库方法列表
```python
Date.prototype.isLeapYear       // 判断闰年

Date.prototype.Format           //日期格式化

Date.prototype.DateAdd          //日期计算

Date.prototype.DateDiff         //比较日期差

Date.prototype.toString         //日期转字符串

Date.prototype.toArray          //日期分割为数组

Date.prototype.DatePart         //取日期的部分信息

Date.prototype.MaxDayOfDate     //取日期所在月的最大天数

Date.prototype.WeekNumOfYear    //判断日期所在年的第几周
```
参考链接：
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date

***
##字符串 
概念：**String** 全局对象是一个用于字符串或一个字符序列的构造函数。字符串用''或""括起来的字符表示。
用 String 函数将其他值生成或转换成字符串：
```python
String(thing)
new String(thing)
//thing——任何可以被转换成字符串的值。
```
###1）长字符串创建：
>* 可以使用 + 运算符将多个字符串连接起来;
>* 可以在每行末尾使用反斜杠字符（“\”），以指示字符串将在下一行继续;

###2）从字符串中获取单个字符

- [ ] 使用 charAt 方法:
```python
    str.charAt(i); // 获取str字符串第i个位置的字符
```
- [ ] 把字符串当作一个类似数组的对象，其中的每个字符对应一个数值索引:
```python
    str[i]; 
```
###3）基本字符串和字符串对象的区别
    字符串字面量 (通过单引号或双引号定义) 和 直接调用 String 方法(没有通过 new 生成字符串对象实例)的字符串都是基本字符串。
    JavaScript会自动将基本字符串转换为字符串对象，只有将基本字符串转化为字符串对象之后才可以使用字符串对象的方法。当基本字符串需要调用一个字符串对象才有的方法或者查询值的时候(基本字符串是没有这些方法的)，JavaScript 会自动将基本字符串转化为字符串对象并且调用相应的方法或者执行查询。
```python
var s_prim = "foo";
var s_obj = new String(s_prim);

console.log(typeof s_prim); // Logs "string"
console.log(typeof s_obj);  // Logs "object"
```
    当使用 eval时，基本字符串和字符串对象也会产生不同的结果。eval 会将基本字符串作为源代码处理; 而字符串对象则被看作对象处理, 返回对象。 例如：
```python
s1 = "2 + 2";               // creates a string primitive
s2 = new String("2 + 2");   // creates a String object
console.log(eval(s1));      // logs the number 4
console.log(eval(s2));      // logs the string "2 + 2"
```
利用 valueOf 方法，我们可以将字符串对象转换为其对应的基本字符串。
```python
console.log(eval(s2.valueOf())); // logs the number 4
```
###模板字面量：
**ES6标准新增的一种多行字符串表示法，用反引号 \` ... \` 表示，内部引用变量用 **${** xxx **}**

```python
`hello world` `hello! world!` `hello ${who}` escape `<a>${who}</a>`
```
#String 对象方法
|方法|	描述|
| --------   | -----:  | 
|anchor()|	创建 HTML 锚。|
|big()|	用大号字体显示字符串。|
|blink()|	显示闪动字符串。|
|bold()|	使用粗体显示字符串。|
|charAt()|	返回在指定位置的字符。|
|charCodeAt()|	返回在指定的位置的字符的 Unicode 编码。|
|concat()|	连接字符串。|
|fixed()	|以打字机文本显示字符串。|
|fontcolor()	|使用指定的颜色来显示字符串。|
|fontsize()	|使用指定的尺寸来显示字符串。|
|fromCharCode()|	从字符编码创建一个字符串。|
|indexOf()	|检索字符串。|
|italics()	|使用斜体显示字符串。|
|lastIndexOf()|	从后向前搜索字符串。|
|link()	|将字符串显示为链接。|
|localeCompare()|	用本地特定的顺序来比较两个字符串。|
|match()|	找到一个或多个正则表达式的匹配。|
|replace()|	替换与正则表达式匹配的子串。|
|search()|	检索与正则表达式相匹配的值。|
|slice()|	提取字符串的片断，并在新的字符串中返回被提取的部分。|
|small()|	使用小字号来显示字符串。|
|split()|	把字符串分割为字符串数组。|
|strike()|	使用删除线来显示字符串。|
|sub()|	把字符串显示为下标。|
|substr()|	从起始索引号提取字符串中指定数目的字符。|
|substring()|	提取字符串中两个指定的索引号之间的字符。|
|sup()	|把字符串显示为上标。|
|toLocaleLowerCase()|	把字符串转换为小写。|
|toLocaleUpperCase()	|把字符串转换为大写。|
|toLowerCase()|	把字符串转换为小写。|
|toUpperCase()|	把字符串转换为大写。|
|toSource()|	代表对象的源代码。|
|toString()	|返回字符串。|
|valueOf()|	返回某个字符串对象的原始值。|
#转义字符
| Code | Output|
| --------   | -----:  | 
|\0	|空字符|
|\'	|单引号|
|\"	|双引号|
|\\	|反斜杠|
|\n	|换行|
|\r	|回车|
|\v	|垂直制表符|
|\t	|水平制表符|
|\b	|退格|
|\f	|换页|
|\uXXXX	|unicode 码|
|\u{X}| ... |
|\u{XXXXXX}|	unicode codepoint |
|\xXX	|Latin-1 字符(x小写)|

参考链接：
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String

***
##正则
**RegExp** 构造函数创建了一个正则表达式对象，用于将文本与一个模式匹配。
创建 RegExp 对象的语法：
```python
/pattern/flags;
new RegExp(pattern [, flags]);
RegExp(pattern [, flags]);
/*** 参数：
    pattern
    正则表达式的文本。
    flags
    如果指定，标志可以具有以下值的任意组合：
    g
    全局匹配;找到所有匹配，而不是在第一个匹配后停止
    i
    忽略大小写
    m
    多行; 将开始和结束字符（^和$）视为在多行上工作（也就是，分别匹配每一行的开始和结束  （由 \n 或 \r 分割），而不只是只匹配整个输入字符串的最开始和最末尾处。
    u
    Unicode; 将模式视为Unicode序列点的序列
    y
    粘性匹配; 仅匹配目标字符串中此正则表达式的lastIndex属性指示的索引(并且不尝试从任何 后续的索引匹配)。
***/
```
***
##Promise 
1. 原理 

2. 实现 

***
##MVVM框架-React、Vue、Angular
1. 组件通信
2. vue-router组件   
3. axios   
4. template编译

###angular自带的工具类函数

   >转换
|API|	描述|
| --------   | -----:  | 
|angular.lowercase()|	将字符串转换为小写|
|angular.uppercase()|	将字符串转换为大写|
|angular.copy()	|数组或对象深度拷贝|
|angular.forEach()|	对象或数组的迭代函数|
    >比较
| API	| 描述 |
| --------   | -----:  | 
|angular.isArray()|	如果引用的是数组返回 true|
|angular.isDate()	|如果引用的是日期返回 true|
|angular.isDefined()|	如果引用的已定义返回 true|
|angular.isElement()	|如果引用的是 DOM 元素返回 true|
|angular.isFunction()|	如果引用的是函数返回 true|
|angular.isNumber()|	如果引用的是数字返回 true|
|angular.isObject()	|如果引用的是对象返回 true|
|angular.isString()	|如果引用的是字符串返回 true|
|angular.isUndefined()|	如果引用的未定义返回 true|
|angular.equals()|	如果两个对象相等返回 true|
    >JSON
|API|	描述|
| --------   | -----:  | 
|angular.fromJson()	|反序列化 JSON 字符串|
|angular.toJson()|	序列化 JSON 字符串|

***
##打包工具-webpack、grunt、gulp
    1. webpack
    2. grunt
    3. gulp
***
##继承 
1. 继承链
2. 实现封装、继承、多态等面向对象的基本功能
3. 使用prototype、function、new、this模拟面向对象的类
https://m.jb51.net/article/107012.html

***
##数据结构
***
##性能优化
***
##兼容
***
##自适应
	屏幕适配
	响应式布局
	
***
##rem
***
##拖拽的实现
	mousedown mousemove mouseup
***
##DOM操作
***
##原生JS封装成组件
>参考链接：
1）封装组件tooltip：https://blog.csdn.net/mobingxiche/article/details/70172952
2）封装轮播图组件：https://www.cnblogs.com/iceman919/p/6192684.html
3）封装hash路由组件：http://www.dengzhr.com/js/1241
4）实现手势解锁组件：https://www.h5jun.com/post/handlock-comp.html
***
##CSS3属性
***
##Ajax
***
##Event Loop
***
##ES6 模块循环加载
***
##文件上传
***
##断点下载
***
##图片 2张
***
##cookie（怎么跨域）
***

