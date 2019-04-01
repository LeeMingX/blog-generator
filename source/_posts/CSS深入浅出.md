---
title: CSS深入浅出
date: 2019-03-29 11:08:54
tags:
---

# css学习方法

## CSS学习难点

1. 在CSS之前是通过标签和属性来控制样式
2. CSS的核心内容：选择器、属性、值
3. html的link标签添加了css的支持，`<link rel='stylesheet' href='xx'>`
4. `<link rel='stylesheet' href='xx' media='print'>`，最早的CSS支持媒体查询功能（向打印的媒介添加样式）
5. 设计原则：需求什么就提供什么
6. 要颜色给 color  要图文混排 float  要绝对定位 position
7. 写CSS不需要复杂的逻辑
8. CSS不正交
    1. 各属性之间互相影响
        * margin合并，在两个div中间加入一个有border样式的div，margin合并会消失，display:table/flex/inline-block 样式也可以使margin合并 padding样式也可以使margin合并 overflow:hidden
        * 小圆点和display，修改display会影响列表的默认小圆点样式
        * 绝对定位之后将元素的display:inline/inline-block改为block
    2. 各元素之间互相影响
        * transform会改变position:fixed的元素
        * float会影响inline元素

## CSS学习简易版

1. 套路即可应付工作
    1. 水平居中
    2. 垂直居中
2. 巧用工具
    1. CSS3 Generator

布局：
    PC：IE8（float布局，所有元素往左浮动，父元素加清除浮动），Flex布局
    Mobile：Flex布局
居中：
    水平居中：子元素宽度不确定（指定左右margin），子元素宽度确定（左右margin为auto），内联元素在父元素写text-align:center
    垂直居中：子元素高度确定（父元素指定上下padding），子元素高度不确定（父元素padding为auto），父元素高度确定（兼容IE-> table div模拟table，chrome+mobile：flex布局）

# CSS核心知识

## 文档流

1. 字和字之间是基线对齐的，设计师在设计字体是会给一个建议行高（字体高度的n倍），即默认行高
2. 在一个div中写一个字母（内联元素），这个div的高度由这个`字体大小*行高`来确定，和字体大小没关系
3. `&nbsp // no break space` 可以在html中添加空格

两行中文左右对齐（头部和尾部各自对齐）

```css
span {
    display: inline-block;
    width: 5em;
    text-align: justify; //两端对齐
    line-height: 20px; //此时font-size为20px
    overflow: hidden;
    height: 20px;
}

span :: after {
    content: '';
    display: inline-block;
    width: 100%;
}
```

html会把内联元素前面和后面的空格都忽略，内联元素之间的空白缩为一个空格

float属性可以清楚内联元素中间的空白，父元素要加clearfix

```css
.clearfix {
    content: '';
    display: block;
    clear: both;
}
```

内联元素在足够多的情况下页面会自动换行，文档流会从左往右移动

`word-break: break-all;` 可以在文字任意位置断开

### 文字溢出处理

多出的文本变成省略号，div中的长度不由文本长度决定

多行多出的文本变成省略号，自查

```css
div {
    border: 1px solid red;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: elipsis;
}
```

```css
div {
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
}
```

### 文字垂直居中

使用`line-height`和`padding`来垂直居中文字，`outline`和`border`比起来不会占用高度，尽量不写高度

### margin合并

如果父元素没有什么东西（border）挡住margin，那么会和子元素的margin合并，通过给父元素的`border-top`和`border-bottom`来实现，或者在父元素上设置padding，`overflow: hidden`也可以取消合并，这种情况子元素的所有内容都不能超过父元素，尽量不使用这种方法

### div中既有内联元素，又有块级元素

div的高度由内部文档流中元素高度的总和决定的。文档流中的内联元素会从左往右排列，碰到边界会换行，块级元素从上到下

`float`会使元素脱离文档流，`position:absolute/fix`也可以将元素脱离文档流，`position:relative;`元素不会脱离文档流，只是参照它原来的位置来定位

### div中的div垂直居中

外部的div高度确定

```css
.dad {
    height: 100vh;
    box-sizing: border-box;
}
.son {
    margin: auto;
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    height: 200px;
    width: 100px;
}
```

外部的div高度不确定

```css
.dad {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

```css
padding-top: 100%; //实现1:1div
```

## 堆叠上下文

### 什么是堆叠顺序

div在屏幕的垂直方向是有层次关系的，这个关系就是堆叠上下文

一个div内，border在background上方，其中的文字/内联元素在border上方，子div是盖不住内联元素的，子div中的文字在父div的文字之上（一般原则，同一类元素，在后面出现的元素会盖住之前的元素）

浮动元素比子div（块级元素）高，浮动元素中的文字没有外部的文字高

相对定位的元素，`position:relative`修饰的元素是最高的，通过改变`z-index`来调整元素垂直方向的高度，`z-index`为正数会变高，如果为负数，且background没有定位的情况下，该元素会在background之下

> 测试堆叠顺序的方法是通过颜色和位置来回测试

### 什么是堆叠上下文

如果父div也有绝对定位，那么子div的负z-index会使子div移动到border之上

堆叠上下文只是一个概念，有一系列描述它的特征，当一个元素满足以下条件是会进入堆叠上下文的状态，否则是默认的展示行为

1. 根元素（HTML）
2. z-index不为`auto`的绝对/相对定位
3. 一个z-index不为`auto`的flex元素（item），父元素为`display:flex|inline-flex`
4. opacity属性值小于1的元素
5. transform属性值不为none的元素
6. mix-blend-mode属性值不为`normal`的元素
7. filter值不为`none`的元素
8. perspective不为`none`的元素
9. isolation的属性被设置为`isolate`的元素
10. `position:fixed`
11. 在will-change中指定了任意CSS属性，即使你没有直接指定这些属性的值
12. `-webkit-overflow:scrolling`属性设置`touch`的元素

一个堆叠上下文比另一个高，那么这个堆叠上下文中的所有元素都会比另一个高