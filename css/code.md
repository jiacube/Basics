### 居中

#### 水平居中

##### 行内元素水平居中

````
.inline-element {
    text-align: center;
}
````

##### 块级元素水平居中

1. margin: 0 auto

````
.item-block-element {
    width: 100px;
    height: 100px;
    border: 1px black solid;
    margin: 0 auto;
}
````

* margin: 0 auto;元素无法水平居中的原因

该元素需要设置一个宽度

该元素不能浮动或绝对定位

DOCTYPE类型相关定义

2. 绝对定位元素结合left和margin实现

必须知道宽度

````
.position-element {
    width: 500px;
    height: 100px;
    position: relative;
}
.item-position-element {
    width: 300px;
    height: 100px;
    position: absolute;
    left: 50%;
    margin-left: -150px;
}
````

#### 行内元素垂直居中

````
.inline-element {
    height: 50px;
    line-height: 50px;
}
````

#### 水平垂直居中

1. 绝对定位+transform

优点：不需要提前知道尺寸

缺点：兼容性不好

````
#container {
    position: relative;
}
#center {
    width: 100px;
    height: 100px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
````

2. 绝对定位+left+margin

缺点：必须知道尺寸

````
#container {
    position: relative;
}
#center {
    width: 80px;
    height: 40px;
    position: absolute;
    left: 50%;
    top: 50%;
    margin-left: -40px;
    margin-top: -20px;
}
````

* 方法3: 绝对定位+margin: auto

优点：不需要提前知道尺寸，兼容性好

````
#container {
    position: relative;
}
#center {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    margin: auto;
}
````

* 方法4: flex

````
#container {
    display: flex;
    justify-content: center;
    align-items: center;
}
````

### 右边宽度固定，左边自适应

1. float + margin

````
<style>
    .right {
        float: right;
        width: 200px;
        height: 200px;
        backgroud-color: rebeccapurple;
    }
    .left {
        height: 200px;
        margin-right: 200px;
        background-color: red;
    }
</style>
<body>
    <div class="right"></div>
    <div class="left"></div>
</body>
````

2. 绝对布局 + margin

````
<style type="text/css">
    .left {
    	width: 100%;
    	height: 100px;
    	position: absolute;
    	right: 200px;
        background-color: green;
    }
    .right {
    	width: 200px;
    	height: 100px;
    	position: absolute;
    	right: 0;
    	background-color: red;
    }	
</style>
<body style="position: relative;">
	<div class="left"></div>
	<div class="right"></div>
</body>
````

3. flex

````
<style>
    body {
        display: -webkit-box;
        display: -moz-box;
        display: -ms-flexbox;
        display: -webkit-flex;
        display: flex;
    }
    .left {
        background-color: rebeccapurple;
        height: 200px;
        flex: 1;
    }
    .right {
        background-color: red;
        height: 200px;
        width: 100px;
    }
</style>
<body>
    <div class="left"></div>
    <div class="right"></div>
</body>
````

4. float + calc

````
<style type="text/css">
    .left {
    	width: calc(100% - 200px);
    	height: 100px;
    	float: left;
    	background-color: green;
    }
    .right {
    	width: 200px;
    	height: 100px;
    	float: left;
    	background-color: red;
    }
</style>
<body>
	<div class="left"></div>
	<div class="right"></div>
</body>
````

### 圣杯布局和双飞翼布局

左右两栏固定宽度，中间部分自适应的三栏布局。

三栏全部float浮动，但左右两栏加上负margin让其跟中间栏div并排，形成三栏布局。

* 圣杯布局和双飞翼布局的不同

双飞翼布局比圣杯布局多创建一个div，但不用相对布局。

* 圣杯布局

````
<style>
    * {
        padding: 0;
        margin: 0;
    }
    body {
        min-width: 650px;
    }
    header {
        height: 100px;
        background-color: red;
    }
    footer {
        height: 100px;
        background-color: aqua;
        clear: both;
    }
    .container > div {
        height: 200px;
        float: left;
    }
    .container {
        padding: 0 250px 0 200px;
        overflow: hidden;
    }
    .center {
        width: 100%;
        background-color: blue;
    }
    .left {
        width: 200px;
        background-color: blueviolet;
        position: relative;
        margin-left: -100%;
        left: -200px;
    }
    .right {
        width: 250px;
        background-color: chartreuse;
        position: relative;
        margin-left: -250px;
        right: -250px;
    }
</style>

<body>
    <header>header</header>
    <div class="container">
        <div class="center">center</div>
        <div class="left">left</div>
        <div class="right">right</div>
    </div>
    <footer>footer</footer>
</body>
````

* 双飞翼布局

````
<style>
    * {
        padding: 0;
        margin: 0;
    }
    header {
        height: 100px;
        background-color: red;
    }
    footer {
        height: 100px;
        background-color: aqua;
        clear: both;
    }
    .main {
        width: 100%;
        float: left;
    }
    .inner-main {
        height: 300px;
        background-color: blue;
        margin-left: 200px;
        margin-right: 250px;
    }
    .left {
        width: 200px;
        height: 300px;
        background-color: blueviolet;
        float: left;
        margin-left: -100%;
    }
    .right {
        width: 250px;
        height: 300px;
        background-color: chartreuse;
        float: left;
        margin-left: -250px;
    }
</style>

<body>
    <header>header</header>
    <div class="main">
        <div class="inner-main">main</div>
    </div>
    <div class="left">left</div>
    <div class="right">right</div>
    <footer>footer</footer>
</body>
````

### 类的实现

* clearfix

````
//伪元素:after
.clearfix:after {
    content: '';
    display: table;
    clear: both;
}
.clearfix {
    *zoom: 1; /* 兼容IE低版本 */
}
````