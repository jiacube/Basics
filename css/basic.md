### CSS选择器
* CSS选择器
* CSS选择器优先级

1.内联样式，如style="XXX"，权值为1000

2.ID选择器，如#content，权值为100

3.类、伪类和属性选择器，如.content、:hover、[attribute]，权值为10

4.元素和伪元素选择器，如div、p，权值为1

5.通用选择器(*)、子选择器(>)和相邻同胞选择器(+)权值为0

### CSS模型
![盒子模型](../images/box.png)
````
//标准模型
box-sizing: content-box;
//IE模型
box-sizing: border-box;
````

### BFC(Block Formatting Context)
#### BFC的原理

* 内部的box会在垂直方向，一个接一个地放置

* 每个元素的margin box的左边与包含块border box的左边相接触(对于从左往右的格式化，否则相反)

* box垂直方向的距离由margin决定，属于同一个BFC的两个相邻box的margin会发生重叠

* BFC的区域不会与浮动区域的box重叠

* BFC是一个页面上的独立的容器，外面的元素不会影响BFC里的元素，反过来，里面的也不会影响外面的。

* 计算BFC高度的时候，浮动元素也会参加计算

#### 创建BFC
* float属性不为none(脱离文档流)

* position为absolute或fixed

* display为inline-block, table-cell, table-caption, inline-flex

* overflow不为visible

* 根元素

#### 应用场景
* 自适应两栏布局

* 消除内部浮动

* 防止垂直margin重叠

### float
破坏性 包裹性 清空格
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
### position
* relative

relative会导致自身位置的相对变化，而不会影响其他元素的位置、大小。

* absolute

1.**absolute元素脱离了文档结构**：和relative不同，其他三个元素的位置重新排列了。只要元素会脱离文档结构，它就会产生破坏性，导致父元素坍塌。

2.**包裹性**：之前<p>的宽度是撑满整个屏幕的，而此时<p>的宽度刚好时内容的宽度。

3.**跟随性**：虽然absolute元素脱离了文档结构，但是它的位置并没有发生变化，还是老老实实地呆在它原本的位置，因为我们此时没有设置top、left的值。

4.absolute元素会悬浮在页面上方，会遮挡住下方的页面内容。

* 定位上下文

1.relative元素的定位永远时相对于**元素自身**设置的，~~和其他元素没关系，也不会影响其他元素~~。

2.fixed元素的定位是相对于**window(或iframe)边界**的，和其他元素没有关系。但是它具有**破坏性**，~~会导致其他元素位置的变化~~。

3.absoulte会递归查找该元素的所有**父元素**，如果找到一个设置了**position:relative/absolute/fixed**的元素，就以该元素为基准定位，如果没找到，就以**浏览器边界**定位。

### flex
![flex布局](../images/flex.png)
* flex-direction设置主轴的方向
row(默认值)：主轴为水平方向，起点在左端。

row-reverse：主轴为水平方向，起点在右边。

column：主轴为垂直方向，起点在上沿。

column-reverse：主轴为垂直方向，起点在下沿。

* justify-content属性定义了项目在主轴上的对齐方式

![justify-content主轴对齐方式](../images/justifyContent.png)

* align-items属性定义项目在交叉轴上如何对齐

stretch(默认值)：如果项目未设置高度或设为auto，将占满整个容器的高度。

![align-items交叉轴对齐方式](../images/alignItems.png)

### 内联元素 块级元素
* 内联元素 display: inline;

a br img input span textarea

* 块级元素 display: block;

div dl(定义列表) form h1 hr ol(排序表单) p table

````
<dl>
    <dt>计算器</dt>
    <dd>用来计算的仪器</dd>
</dl>

<ol start="7">
    <li>Tea</li>
</ol>
````
### 居中
* 水平居中
````
//行内元素
.inline-element {
    text-align: center;
}
//块级元素
.block-element {
    text-align: center;
}
.item-block-element {
    width: 1000px;
    margin: auto;
}
//绝对定位元素结合left和margin实现，但是必须知道宽度
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
* 垂直居中
````
//行内元素
.inline-element {
    height: 50px;
    line-height: 50px;
}
//绝对定位元素，可结合left和margin实现，但是必须知道尺寸
.position-element {
    position: relative;
    height: 200px;
}
.item-position-element {
    width: 80px;
    height: 40px;
    position: absolute;
    left: 50%;
    top: 50%;
    margin-left: -40px;
    margin-top: -20px;
}
/*
    绝对定位可结合transform实现居中
    优点：不需要提前知道尺寸
    缺点：兼容性不好
*/
.transform-element {
    position: relative;
    height: 200px;
}
.item-transform-element {
    width: 80px;
    height: 40px;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
}
//绝对定位结合margin: auto，不需要提前知道尺寸，兼容性好
.margin-auto-element {
    position: relative;
    height: 200px;
}
.item-margin-auto-element {
    width: 100px;
    height: 50px;
    position: absolute;
    left: 0;
    top: 0;
    right: 0;
    bottom: 0;
    margin: auto;
}
````