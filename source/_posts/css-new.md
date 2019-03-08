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