### HTML5新增标签

header footer hgroup nav audio video canvas

* figure figcaption

figure元素的内容应该与主内容相关，但如果被删除，则不应对文档流产生影响。

figcaption标签定义figure元素的标题(caption)。figcaption元素应该被置于"figure"元素的第一个或最后一个子元素的位置。

EX: 用作文档中插图的图像

````
<figure>
    <img src="yxq.png" alt="chz" width="300" height="250"/>
    <figcaption>Chz Love YXQ</figcaption>
</figure>
````

* article

来自一个外部的新闻提供者的一篇新的文章，或者来自blog的文本，或者是来自论坛的文本。亦或是来自其他外部源内容。

* section

定义文档中的节(section、区段)，比如章节、页眉、页脚或文档中的其他部分。

* aside

article以外的内容，可用作article的侧栏

* source

为媒介元素(video/audio)定义媒介资源

规定可替换的视频/音频文件供浏览器根据它对媒体类型或者解码器的支持进行选择

````
<audio controls>
    <source src="yxq.ogg" type="audio/ogg"/>
    <source src="yxq.mp3" type="audio/mpeg"/>
    Your browser does not support the audio element.
</audio>
````

### HTML5 新的input类型

email   url   number   range   Date pickers(date, month, week, time, datetime, datetime-local)   search   color

### HTML5语义化

参考链接: https://www.jianshu.com/p/6bc1fc059b51

根据内容的结构化(内容语义化)，选择合适的标签(代码语义化)，便于开发者阅读和写出更优雅的代码的同时让浏览器的爬虫和机器很好地解析。

* 语义化的优点

有利于SEO：和搜索引擎建立良好沟通，有助于爬虫抓取更多的有效信息：爬虫依赖于标签来确定上下文和各个关键字的权重

方便其他设备解析(如屏幕阅读器、盲人阅读器、移动设备)以有意义的方式来渲染网页

为了在没有CSS的情况下，页面也能呈现出很好的内容结构、代码结构: 为了裸奔时好看

便于团队开发和维护，语义化更具有可读性

* 语义化标签

header footer hgroup nav article aside section figure figcaption address

### a标签

* 目标target

![target](images/target.png)

### defer | async

script标签用于加载和执行脚本。

async和defer使script都不会阻塞DOM的渲染。

**defer**属性规定是否对脚本执行延迟，直到页面加载为止。

只有Internet Explorer支持defer属性。

**async**属性规定一旦脚本可用，则会异步执行。

async的执行，并不会按照script在页面中的顺序来执行，而是谁先加载完谁先执行。

### 浏览器内核

Trident(IE) Gecko(Firfox) Blink(Chrome) Webkit(Safari)

浏览器内核分为渲染引擎、JS引擎两部分

渲染引擎：DOM Tree -> CSS Tree -> Render Tree -> 布局(Layout) -> 绘制(Paint) -> 复合图层化

### 重绘和回流

*重绘*: 当页面中元素样式的改变并不影响它在文档流中的位置时(EX:color|visibility)，浏览器会将新样式赋予给元素并重新绘制它。

*回流*: 当Render Tree(DOM)中部分或全部元素的尺寸、结构或某些属性发生改变时，浏览器重新渲染部分或全部文档的过程。

回流要比重绘消耗性能开支更大。

回流必将引起重绘，重绘不一定引起回流。

