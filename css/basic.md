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
