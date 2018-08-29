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

**vue:**http://www.php.cn/js-tutorial-386469.html
**React:**https://www.jianshu.com/p/fb915d9c99c4
**angular2+:**https://blog.csdn.net/yaomengzhi/article/details/80277702
**angualr1:**https://www.cnblogs.com/myzhibie/p/5745018.html

2. vue-router组件 

官方文档：https://router.vuejs.org/zh/guide/
参考：https://www.cnblogs.com/SamWeb/p/6610733.html

3. axios  

参考（中文）：https://www.kancloud.cn/yunye/axios/234845
参考（英文）：https://www.npmjs.com/package/axios

4. template编译


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
<tr><td> API	</td>	<td>描述 </td></tr>
<tr><td>angular.isArray()</td>	<td>	如果引用的是数组返回 true</td></tr>
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
**继承 **

1. 继承链
2. 实现封装、继承、多态等面向对象的基本功能
3. 使用prototype、function、new、this模拟面向对象的类
https://m.jb51.net/article/107012.html

***

**数据结构**

***

**性能优化**

***

**兼容**

***

**自适应**
	屏幕适配
	响应式布局
	
***

**rem**

***

**拖拽的实现**

	mousedown mousemove mouseup
	
***

**DOM操作**

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

***

**ES6 模块循环加载**

***

**文件上传**

***

**断点下载**

***

**图片 2张**

***

**cookie（怎么跨域）**

***
