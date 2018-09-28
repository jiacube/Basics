日期

日期常规操作
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

日期时间脚本库方法列表
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


**字符串 **

概念：**String** 全局对象是一个用于字符串或一个字符序列的构造函数。字符串用''或""括起来的字符表示。
用 String 函数将其他值生成或转换成字符串：
```python
String(thing)
new String(thing)
//thing——任何可以被转换成字符串的值。
```
1）长字符串创建：
>* 可以使用 + 运算符将多个字符串连接起来;
>* 可以在每行末尾使用反斜杠字符（“\”），以指示字符串将在下一行继续;

2）从字符串中获取单个字符

- [ ] 使用 charAt 方法:
```python
    str.charAt(i); // 获取str字符串第i个位置的字符
```
- [ ] 把字符串当作一个类似数组的对象，其中的每个字符对应一个数值索引:
```python
    str[i]; 
```
3）基本字符串和字符串对象的区别
    字符串字面量 (通过单引号或双引号定义) 和 直接调用 String 方法(没有通过 new 生成字符串对象实例)的字符串都是基本字符串。
    JavaScript会自动将基本字符串转换为字符串对象，只有将基本字符串转化为字符串对象之后才可以使用字符串对象的方法。当基本字符串需要调用一个字符串对象才有的方法或者查询值的时候(基本字符串是没有这些方法的)，JavaScript 会自动将基本字符串转化为字符串对象并且调用相应的方法或者执行查询。
```python
var s_prim = "foo";
var s_obj = new String(s_prim);

console.log(typeof s_prim); // Logs "string"
console.log(typeof s_obj);  // Logs "object"
```
**当使用 eval时，基本字符串和字符串对象也会产生不同的结果。eval 会将基本字符串作为源代码处理; 而字符串对象则被看作对象处理, 返回对象。 例如：**
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

**模板字面量：**

**ES6标准新增的一种多行字符串表示法，用反引号 \` ... \` 表示，内部引用变量用 **${** xxx **}** 

```python
`hello world` `hello! world!` `hello ${who}` escape `<a>${who}</a>`
```

**String 对象方法**

<table>
	<tr><td>方法</td>	<td>描述</td></tr>
<tr><td>anchor()</td>	<td>创建 HTML 锚。</td></tr>
<tr><td>big()</td>	<td>	用大号字体显示字符串。</td></tr>
<tr><td>blink()</td>	<td>	显示闪动字符串。</td></tr>
<tr><td>bold()</td>	<td>	使用粗体显示字符串。</td></tr>
<tr><td>charAt()</td>	<td>	返回在指定位置的字符。</td></tr>
<tr><td>charCodeAt()</td>	<td>	返回在指定的位置的字符的 Unicode 编码。</td></tr>
<tr><td>concat()</td>	<td>	连接字符串。</td></tr>
<tr><td>fixed()	</td>	<td>以打字机文本显示字符串。</td></tr>
<tr><td>fontcolor()	</td>	<td>使用指定的颜色来显示字符串。</td></tr>
<tr><td>fontsize()	</td>	<td>使用指定的尺寸来显示字符串。</td></tr>
<tr><td>fromCharCode()</td>	<td>	从字符编码创建一个字符串。</td></tr>
<tr><td>indexOf()	</td>	<td>检索字符串。</td></tr>
<tr><td>italics()	</td>	<td>使用斜体显示字符串。</td></tr>
<tr><td>lastIndexOf()</td>	<td>从后向前搜索字符串。</td></tr>
<tr><td>link()	</td>	<td>将字符串显示为链接。</td></tr>
<tr><td>localeCompare()</td>	<td>	用本地特定的顺序来比较两个字符串。</td></tr>
<tr><td>match(</td>	<td>	找到一个或多个正则表达式的匹配。</td></tr>
<tr><td>replace()</td>	<td>	替换与正则表达式匹配的子串。</td></tr>
<tr><td>search()</td>	<td>	检索与正则表达式相匹配的值。</td></tr>
<tr><td>slice()</td>	<td>	提取字符串的片断，并在新的字符串中返回被提取的部分。</td></tr>
<tr><td>small()</td>	<td>	使用小字号来显示字符串。</td></tr>
<tr><td>split()</td>	<td>	把字符串分割为字符串数组。</td></tr>
<tr><td>strike()</td>	<td>	使用删除线来显示字符串。</td></tr>
<tr><td>sub()</td>	<td>	把字符串显示为下标。</td></tr>
<tr><td>substr()</td>	<td>	从起始索引号提取字符串中指定数目的字符。</td></tr>
<tr><td>substring()</td>	<td>	提取字符串中两个指定的索引号之间的字符。</td></tr>
<tr><td>sup()	</td>	<td>把字符串显示为上标。</td></tr>
<tr><td>toLocaleLowerCase()</td>	<td>	把字符串转换为小写。</td></tr>
<tr><td>toLocaleUpperCase()	</td>	<td>把字符串转换为大写。</td></tr>
<tr><td>toLowerCase()</td>	<td>	把字符串转换为小写。</td></tr>
<tr><td>toUpperCase()</td>	<td>	把字符串转换为大写。</td></tr>
<tr><td>toSource()</td>	<td>	代表对象的源代码。</td></tr>
<tr><td>toString()	</td>	<td>返回字符串。</td></tr>
<tr><td>valueOf()</td>	<td>	返回某个字符串对象的原始值。</td></tr>
	</table>
	
**转义字符**

<table>
<tr><td> Code </td>	<td> Output</td></tr>
<tr><td>\0	</td>	<td>空字符</td></tr>
<tr><td>\'	</td>	<td>单引号</td></tr>
<tr><td>\"	</td>	<td>双引号</td></tr>
<tr><td>\\	</td>	<td>反斜杠</td></tr>
<tr><td>\n	</td>	<td>换行</td></tr>
<tr><td>\r	</td>	<td>回车</td></tr>
<tr><td>\v	</td>	<td>垂直制表符</td></tr>
<tr><td>\t	</td>	<td>水平制表符</td></tr>
<tr><td>\b	</td>	<td>退格</td></tr>
<tr><td>\f	</td>	<td>换页</td></tr>
<tr><td>\uXXXX	</td>	<td>unicode 码</td></tr>
<tr><td>\u{X}</td>	<td> ... </td></tr>
<tr><td>\u{XXXXXX}</td>	<td>	unicode codepoint </td></tr>
<tr><td>\xXX	</td>	<td>Latin-1 字符(x小写)</td></tr>
	</table>

参考链接：
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String

***

**正则**

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


**Promise **


参考链接：
http://es6.ruanyifeng.com/#docs/promise

1. 原理 

   Promise 对象用于延迟(deferred) 计算和异步(asynchronous )计算.一个Promise对象代表着一个还未完成，但预期将来会完成的操作。Promise 对象是一个返回值的代理，这个返回值在promise对象创建时未必已知。它允许你为异步操作的成功或失败指定处理方法。 这使得异步方法可以像同步方法那样返回值：异步方法会返回一个包含了原返回值的 promise 对象来替代原返回值。
   
 Promise 对象用来进行延迟( deferred )和异步( asynchronous )计算。一个 Promise 处于以下四种状态之一: 
- pending: 还没有得到肯定或者失败结果，进行中 
- fulfilled: 成功的操作 
- rejected: 失败的操作 
- settled: 已被 fulfilled 或 rejected
 
2. 实现 

***

**MVVM框架-React、Vue、Angular**

1. 组件通信
- vue: http://www.php.cn/js-tutorial-386469.html
- React: https://www.jianshu.com/p/fb915d9c99c4
- angular2+: https://blog.csdn.net/yaomengzhi/article/details/80277702
- angualr1: https://www.cnblogs.com/myzhibie/p/5745018.html

2. vue-router组件 

- 官方文档：https://router.vuejs.org/zh/guide/
- 参考：https://www.cnblogs.com/SamWeb/p/6610733.html

3. axios  

- 参考（中文）：https://www.kancloud.cn/yunye/axios/234845
- 参考（英文）：https://www.npmjs.com/package/axios

4. template编译

***


**angular自带的工具类函数**


   **转换**
   
<table>
<tr><td>API</td>	<td>	描述</td></tr>
<tr><td>angular.lowercase()</td>	<td>	将字符串转换为小写</td></tr>
<tr><td>angular.uppercase()</td>	<td>	将字符串转换为大写</td></tr>
<tr><td>angular.copy()	</td>	<td>数组或对象深度拷贝</td></tr>
<tr><td>angular.forEach()</td>	<td>	对象或数组的迭代函数</td></tr>
</table>
	
   **比较**
   
<table>
<tr><td> API</td>	<td>描述 </td></tr>
<tr><td>angular.isArray()</td><td>	如果引用的是数组返回 true</td></tr>
<tr><td>angular.isDate()	</td>	<td>如果引用的是日期返回 true</td></tr>
<tr><td>angular.isDefined()</td>	<td>	如果引用的已定义返回 true</td></tr>
<tr><td>angular.isElement()	</td>	<td>如果引用的是 DOM 元素返回 true</td></tr>
<tr><td>angular.isFunction()</td>	<td>	如果引用的是函数返回 true</td></tr>
<tr><td>angular.isNumber()</td>	<td>	如果引用的是数字返回 true</td></tr>
<tr><td>angular.isObject()	</td>	<td>如果引用的是对象返回 true</td></tr>
<tr><td>angular.isString()	</td>	<td>如果引用的是字符串返回 true</td></tr>
<tr><td>angular.isUndefined()</td>	<td>	如果引用的未定义返回 true</td></tr>
<tr><td>angular.equals()</td>	<td>	如果两个对象相等返回 true</td></tr>
</table>

 **JSON** 
 
<table>
<tr><td>API</td>	<td>	描述</td></tr>
<tr><td>angular.fromJson()	</td>	<td>反序列化 JSON 字符串</td></tr>
<tr><td>angular.toJson()</td>	<td>	序列化 JSON 字符串</td></tr>
	</table>

***

**打包工具-webpack、grunt、gulp**

    1. webpack
    2. grunt
    3. gulp
***
**继承**

1. 继承链
2. 实现封装、继承、多态等面向对象的基本功能
3. 使用prototype、function、new、this模拟面向对象的类
https://m.jb51.net/article/107012.html

***

**数据结构**
- 栈：一种遵从先进后出 (LIFO) 原则的有序集合；新添加的或待删除的元素都保存在栈的末尾，称作栈顶，另一端为栈底。在栈里，新元素都靠近栈顶，旧元素都接近栈底。
- 队列：与上相反，一种遵循先进先出 (FIFO / First In First Out) 原则的一组有序的项；队列在尾部添加新元素，并从头部移除元素。最新添加的元素必须排在队列的末尾。
- 链表：存储有序的元素集合，但不同于数组，链表中的元素在内存中并不是连续放置的；每个元素由一个存储元素本身的节点和一个指向下一个元素的引用（指针/链接）组成。
- 集合：由一组无序且唯一（即不能重复）的项组成；这个数据结构使用了与有限集合相同的数学概念，但应用在计算机科学的数据结构中。
- 字典：以 [键，值] 对为数据形态的数据结构，其中键名用来查询特定元素，类似于 Javascript 中的Object。
- 散列：根据关键码值（Key value）直接进行访问的数据结构；它通过把关键码值映射到表中一个位置来访问记录，以加快查找的速度；这个映射函数叫做散列函数，存放记录的数组叫做散列表。
- 树：由 n（n>=1）个有限节点组成一个具有层次关系的集合；把它叫做“树”是因为它看起来像一棵倒挂的树，也就是说它是根朝上，而叶朝下的，基本呈一对多关系，树也可以看做是图的特殊形式。
- 图：图是网络结构的抽象模型；图是一组由边连接的节点（顶点）；任何二元关系都可以用图来表示，常见的比如：道路图、关系图，呈多对多关系。
[作者：Surmon，链接：https://juejin.im/post/594dfe795188250d725a220a，来源：掘金]
***

**性能优化**
- 减少 HTTP请求数：合理设置 HTTP缓存，资源合并与压缩，CSS Sprites，Inline Images，Lazy Load Images；
- 将 CSS放在头部（head中）；
- 将外部脚本置底；
- Lazy Load Javascript：异步执行inline脚本；
- 异步请求Callback；
- 减少不必要的 HTTP跳转；
- 避免重复的资源请求；
- 减少DOM操作；避免HTML Collection，当需要HTML Collection，遍历的时候，尽量将它转为数组后再访问，以提高性能；避免Reflow & Repaint（重绘和重排）；
- 慎用低性能js方法或语句：慎用 with，避免使用 eval和 Function，减少作用域链查找，减少全局变量，join代替“+”;
- CSS：避免嵌套过深，Image压缩等
***

**兼容**
- 引入html5shiv解决浏览器兼容问题：
```python
 <!--[if lt IE 9]>
  <script src="http://apps.bdimg.com/libs/html5shiv/3.7/html5shiv.min.js"></script>
 <![endif]-->
 ```
 - cssHacks: 
 	1)条件注释法;
	
	只在IE下生效
	<!--[if IE]>
	这段文字只在IE浏览器显示
	<![endif]-->
	
	只在IE6下生效
	<!--[if IE 6]>
	这段文字只在IE6浏览器显示
	<![endif]-->
	
	2)类内属性前缀法;
	
	“-″减号是IE6专有的hack
	“\9″ IE6/IE7/IE8/IE9/IE10都生效
	“\0″ IE8/IE9/IE10都生效，是IE8/9/10的hack
	“\9\0″ 只对IE9/IE10生效，是IE9/10的hack
	
	3)选择器前缀法;
	
	*html *前缀只对IE6生效
	*+html *+前缀只对IE7生效
	@media screen\9{...}只对IE6/7生效
	@media \0screen {body { background: red; }}只对IE8有效
	@media \0screen\,screen\9{body { background: blue; }}只对IE6/7/8有效
	@media screen\0 {body { background: green; }} 只对IE8/9/10有效
	@media screen and (min-width:0\0) {body { background: gray; }} 只对IE9/10有效
	@media screen and (-ms-high-contrast: active), (-ms-high-contrast: none) {body { background: orange; }} 只对IE10有效
	等等

***

**自适应**
	- 屏幕适配
	<!-- 视口 -->
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	详解：width=device-width 把布局视口设置成为浏览器（屏幕）的宽度;
	     initial-scale=1 初始缩放的比例是1，使用它的时候，同时也会将布局视口的尺寸设置为缩放后的尺寸。
	- 响应式布局
	什么是响应式？同一个页面在不同屏幕尺寸下有不同的布局。
	响应式设计方案：
		CSS3 Media Query（推荐）：媒体查询，兼容到IE9+，但可以通过插件兼容IE6-8（利用@media规则为主要手段），如respond.js和css3-mediaqueries-js；
		Flex：弹性布局，兼容性较差（IE10+）
		Grid：网格布局，兼容性更差
		Columns：栅格系统，往往需要依赖于某个UI库，如bootstrap
		【响应式开发避免杂合使用rem】

响应式和自适应的区别：	
	响应式针对的是不同分辨率设备而进行的适配式设计，以利用@media规则为主要手段，而自适应则忽略@media以比例布局为主，目的是适应不同的浏览器窗口大小。
	
***

**rem**
px、em、rem之间的关系：
- px：像素是相对于显示器屏幕分辨率而言的相对长度单位。pc端使用px倒也无所谓，可是在移动端，因为手机分辨率种类颇多，不可能一个个去适配，这时px就显得非常无力，所以就要考虑em和rem。
- em：是相对长度单位，相对于当前对象内文本的字体尺寸，即em的计算是基于父级元素font-size的。假设html的font-size默认为16px，body字体大小定义为50%，那么在body里字体大小就是1em=8px了。可当你又定义了一个div，然后把字体设置成了50%，请问，现在div下的1em等于多少？因为继承了父级的值，现在这个div里的1em=4px...
- rem：是em的升级版，rem是相对于html根元素的(在body标签里面设置字体大小不起作用)，不会受到父级的影响，这样的好处在于：从em里的例子来讲，1rem始终会等于8px。使用的时候不需要重新计算rem此时的大小。rem因为是css3增加的，所以ie8或以下请无视。（浏览器默认的字体大小都是16px）

[引用来源：https://my.oschina.net/thinkive/blog/669942]
***

**拖拽的实现**

参考：https://juejin.im/entry/59eebc39f265da431c6f7bdb；
      https://juejin.im/post/5a667e286fb9a01c982cb474

	
***

**原生JS封装成组件**

>参考链接：
1）封装组件tooltip：https://blog.csdn.net/mobingxiche/article/details/70172952
2）封装轮播图组件：https://www.cnblogs.com/iceman919/p/6192684.html
3）封装hash路由组件：http://www.dengzhr.com/js/1241
4）实现手势解锁组件：https://www.h5jun.com/post/handlock-comp.html
***

**CSS3属性**

***

**Ajax**

***

**Event Loop**
JavaScript 是单线程的，浏览器是多进程的。于是，JavaScript 的任务可以分为同步任务和异步任务。
 Event Loop 机制：
 1)所有同步任务都在主线程上执行，形成一个执行栈
 2)主线程之外，事件触发线程管理着一个任务队列，只要异步任务有了运行结果，就在任务队列之中放置一个事件。
 3)一旦执行栈中的所有同步任务执行完毕（此时JS引擎空闲），系统就会读取任务队列，将可运行的异步任务添加到执行栈中，开始执行。

***

**ES6 模块循环加载**
"循环加载"（circular dependency）指的是，a脚本的执行依赖b脚本，而b脚本的执行又依赖a脚本，存在强耦合。
ES6模块的运行机制与CommonJS不一样，它遇到模块加载命令import时，不会去执行模块，而是只生成一个引用。等到真的需要用到时，再到模块里面去取值。因此，ES6模块是动态引用，不存在缓存值的问题，而且模块里面的变量，绑定其所在的模块。
[引用来源：http://www.ruanyifeng.com/blog/2015/11/circular-dependency.html]
***

**文件上传**
上传插件：Web Uploader、JSAjaxFIleUploader、jQuery-File-Upload。
通常上传控件向下兼容的方案通常是高版本浏览器采用ajax方式，低版本浏览器采用iframe+form表单形式。
- iframe封装form表单上传：
form表单属性中action属性规定后端处理文件上传的路径；method属性规定上传文件的方法post or get；enctype属性规定在发送到服务器之前应该如何对表单数据进行编码，在使用包含文件上传控件的表单时必须使用“multipart/form-data”。但是上传同步、上传完成页面会刷新，实现文件异步上传，只能通过iframe+form。
iframe+form实现原理：
文件上传时在页面中动态创建一个iframe元素和一个form元素，并将form元素的target属性指向动态创建iframe元素。当用户完成选择文件动作时，提交子页面中的 form。这时，iframe跳转，而父页面没有刷新。这使得上传结束后，服务器处理结果返回到动态iframe窗口而没有刷新页面

[引用链接：https://www.jianshu.com/p/374e9b9d1fb1]

***

**断点下载**

***

**图片 2张**

***

**cookie（怎么跨域）**

***
