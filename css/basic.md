### CSS选择器
* CSS选择器
![CSS选择器](../images/cssSelector1.png)
![CSS选择器](../images/cssSelector2.png)
link visited hover active
![CSS选择器](../images/cssSelector3.png)
![CSS选择器](../images/cssSelector4.png)
![CSS选择器](../images/cssSelector5.png)

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

### BFC(Block Formatting Context) 块级格式化上下文

独立的渲染区域，只有Block-level box参与，它规定了内部的Block-level Box如何布局，并且与这个区域外部毫不相关。

#### BFC布局规则

* 内部的box会在垂直方向，一个接一个地放置

* box垂直方向的距离由margin决定，属于同一个BFC的两个相邻box的margin会发生重叠

* 每个元素的margin box的左边，与包含块border box的左边相接触(对于从左往右的格式化，否则相反)。即使存在浮动也是如此。

* BFC的区域不会与float box重叠

* BFC是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外部的元素。反之也如此。

* 计算BFC高度的时候，浮动元素也会参与计算

#### 创建BFC
* 根元素

* float属性不为none(脱离文档流)

* position为absolute或fixed

* display为inline-block, table-cell, table-caption, inline-flex

* overflow不为visible

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

### Flex(弹性)布局 一维

![Flex布局](../images/flex.png)

#### 容器的属性

* flex-direction设置主轴的方向
row(默认值)：主轴为水平方向，起点在左端。

row-reverse：主轴为水平方向，起点在右边。

column：主轴为垂直方向，起点在上沿。

column-reverse：主轴为垂直方向，起点在下沿。

* flex-wrap属性定义如果一条轴线排不下，如何换行。

flex-wrap: nowrap | wrap | wrap-reverse

* flex-row属性时flex-direction属性和flex-wrap属性的简写形式。

* justify-content属性定义了项目在主轴上的对齐方式

![justify-content主轴对齐方式](../images/justifyContent.png)

* align-items属性定义项目在交叉轴上如何对齐

stretch(默认值)：如果项目未设置高度或设为auto，将占满整个容器的高度。

![align-items交叉轴对齐方式](../images/alignItem.png)

* align-content属性定义了多根轴线的对齐方式。

align-content: flex-start | flex-end | center | space-between | space-around | stretch;

#### 项目的属性

* order属性定义项目的排列顺序

* flex-grow属性定义项目的放大比例

* flex-shrink属性定义了项目的缩小比例

* flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间。

* flex属性是flex-grow, flex-shrink, flex-basis的简写。

* align-self属性允许单个项目有与其他项目不一样的对齐方式

align-self: auto | flex-start | flex-end | center | baseline | stretch

### Grid(网格)布局 二维

Grid布局由两个核心组成部分wrapper(父元素)和items(子元素)。wrapper是实际的grid(网格)，items是grid(网格)内的内容。

定义列和行：grid-template-row grid-template-column

定位和调整items(子元素)大小：grid-column grid-row

````
.wrapper {
    display: grid;
    grid-template-columns: 100px 100px 100px;
    grid-template-rows: 50px 50px;
}
.item1 {
    grid-column: 1 / 4;
}
.item3 {
    grid-row-start: 2;
    grid-row-end: 4;
}
.item4 {
    grid-column-start: 2;
    grid-column-end: 4;
}
````

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

### 伪类 伪元素

* 伪类本质上是为了弥补常规CSS选择器的不足，以便获取到更多信息

* 伪元素本质上是创建了一个有内容的虚拟容器

* CSS3中伪类和伪元素的语法不同

* 可以同时使用多个伪类，而只能同时使用一个伪元素

CSS伪类用于向某些选择器添加特殊的效果。
![伪类](../images/pseudoClass.png)

CSS伪元素用于将特殊的效果添加到某些选择器。
![伪元素](../images/pseudoElement.png)

1. :link :visited :hover :active伪类

link: 用于选取未被访问的链接

visited: 对指向已访问页面的链接设置样式

hover: 用于设置鼠标指针浮动到链接上时的样式

active: 用于设置点击链接时的样式

**爱恨(LoVe/HAte)**

**CSS的就近原则**：

当鼠标经过未访问的链接，会同时拥有a:link、a:hover两种属性，a:link离它最近，所以它优先满足a:link，而放弃a:hover的重复定义。

当鼠标经过已经访问过的链接，会同时拥有a:visited、a:hover两种属性，a:visited离它最近，所以它优先满足a:visited，而放弃a:hover的重复定义。