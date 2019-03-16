---
title: css-new
date: 2019-03-08 20:32:01
tags:
---

# CSS

## CSS的历史

Cascading Style Sheets 层叠样式表

1998年CSS2.1开始CSS流行起来，支持最广，现在从IE8测试兼容

2011年CSS3被分为多个模块单独升级，统称为CSS3

## CSS学习资源

1. MDN文档
2. CSSTricks
3. 阮一峰CSS
4. 张鑫旭CSS
5. Codrops炫酷效果
6. CSS揭秘
7. CSS2.1 spec

## 引用CSS的方法

在html的标签中设置属性可以修改元素样式，`<font></font>/<center></center>`这种标签也可以修改样式，但是都被废弃掉了，现在通过style属性来为标签设置样式

内联样式：把style属性写在标签上
style标签
外联样式/外部文件：`<link rel="stylesheet" href="xx.css">`
CSS文件中请求另一个CSS：`@import url(b.css)`

## float

列表横向排列：所有列表子元素(`<li>`)加`float: left`，这样会有bug，然后通过浮动元素的父元素加一个类`clearfix`，可以消除bug的效果

```css
.clearfix::after {
    content: '';
    display: block;
    clear: both;
}
```

## 继承属性

color属性可以继承，默认继承顶层标签规定样式，浏览器有预设样式

## 对齐

将元素的高度调成一致的，然后通过`padding`属性来控制内容的对齐（中线对齐）

## 选择器

`x > y > z {}` 表示y必须是x的子代，z必须是y的子代
`.x .y .z {}` 表示y类需要在x类里， z类需要在y类里

## 一个元素的高度

块级元素高度由其内部文档流元素的高度综合决定的

> 文档流：文档内元素的流动方向

内联元素由左往右流动，遇到阻碍换行继续流动

块级元素，每个元素占一行，由上往下

内联元素的流动特点：中文的字在流动过程中遇到阻碍，以`span`为例，可能会出现一部分字到了第二行，另一部分还停留在第一行，但是英文（单词）不会出现这种情况，如果需要英文也按字母来流动，可以通过设置元素属性`word-break: break-all`来实现

如果需要块级元素在同一行显示，那么可以给元素一个`display: inline-block`的属性（CSS3）来实现

### 内联元素的高度由什么决定？

所有的字体有一条基线，四线谱的第三根线为基线，文字对齐是以基线对齐，每个字体有建议的行高

`font-size: 100px`的含义是字体最高字母的最上面到最低字母的最下面，

可以使用`line-height: 100px`来指定行高

div中有多个span时，最高的span多高，决定div的高度

内联元素高度不可控，需要指定height

使用`height`很容易出问题

让某一个元素脱离文档流，使用`position: fix`，

位置fix之后，元素的宽度会缩小，通过设置`width: 100%`来扩大，这种用法会有bug

height/width 最好不用

内联元素左右padding没有用，上下padding有用，居中需要设置父元素的`text-align: center`

### 给背景图片加一个透明效果

在图片上加一个div，设置`background-color: rgb(0,0,0,0.8)`

### 图片居中

`background-position: center center #水平方向，垂直方向`

### 背景图片和div自适应

通过`background-size: cover`来设置图片与div自适应

`max-width`设置的宽度在屏幕尺寸缩小时会自适应，如果div有一个宽度，那么让它居中可以设置`margin-left: auto; margin-right auto;`

> span不接受设置的宽高

`display: inline-block`不会和div的p的边框合并

### iconfont.cn

### vertical-align: top要配合inline-block使用

svg图在div中会偏上，设置此属性可以正常

### content-box和border-box的区别

`box-sizing`属性定义浏览器如何计算一个元素的全宽和全高

content-box为浏览器默认行为，只计算元素内容宽高，不包括padding, border, or margin，边框会加到最终渲染宽度，border-box会使计算机计算任一个元素的边框进元素宽高，包括 the content, padding, and border, but do not include the margin

## 伪元素

断子绝孙的元素就是空元素

所有的非空标签都有伪类，`::before`和`::after`

创建一个伪元素，是选择元素的第一个子元素，经常通过content守护星被用来加装饰性内容到该元素，默认这个元素是inline的

`position: absolute`给定之后自动显示为block

### 如果父元素高度确定，则子元素可以直接写100%

## 伪类

表状态的类都是伪类，在特定情况下才能被选中 `:hover`类似

## 类选择器和ID选择器

类选择器选择一类相同特性的元素，id选择器选择唯一的元素