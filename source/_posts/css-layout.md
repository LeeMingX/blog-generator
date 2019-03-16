---
title: css-layout
date: 2019-03-14 03:06:44
tags:
---

# CSS布局

> 翻译自[CSS-trick(centering-css-complete-guide)](https://css-tricks.com/centering-css-complete-guide/)

## 左右布局

1. 使用背景色渐变

    ```css
    .container {
        background: linear-gradient(
            to right,
            #ff9e2c 0%,
            #ff9e2c 50%,
            #b6701e 50%,
            #b6701e 100%
        )
    }
    ```

    根据控制颜色渐变的位置来划分出左右两部分

    这种做法作用于一个容器元素，如果需要在左右都添加内容，那么需要配合`float`来操作

2. 使用绝对定位

    ```css
    .parent {
        position: relative;
    }
    .child1,
    .child2 {
        position: absolute;
    }
    ```

    使用绝对定位使两个子元素位于左右两边

    这种做法比较简单，但是这样父元素需要指定`height`，而指定了height又会影响元素中的内容展示，并且绝对定位使得元素脱离了文档流，那么需要展示在这些元素下面的内容编排又是大问题。

3. 使用Table

    一行两列的表结构，这种方式基本不用，不赘述

4. 使用float

    ```css
    .parent {
        display: block;
        content: "";
        clear: both;
    }
    .child1,
    .child2 {
        float: left;
    }
    ```

    两个子元素设置`float:left`，父元素设置`clear float`的属性，即可完成左右布局

    避免了绝对定位的尴尬，要记得父元素的`clear float`

5. 使用inline-block

    通过将元素设置为`display:inline-block`可以使元素在一行内展示，但是要确认元素之间没有其它内容，否则会出现间隙，可以避免`float`之后再清除`float`，但是需要配合`vertical-align:top`使用，否则高度会有问题

6. 使用Flex
7. 使用Grid

> 6/7两种方式在学习过后再补充

## 左中右布局

左中右布局可以分解为左一元素+右二元素，右二元素再分为左一元素和右一元素

## 水平居中

1. 对于`inline, inline-block, inline-table, inline-flex, inline-*`这些元素，`text-align: center;`可以将元素水平居中的效果

2. 对于块级元素，可以通过设置`margin: 0 auto`来将元素居中，前提是这个元素被设置了宽度，宽度等于屏幕宽度就没有了居中的概念

3. 多个块级元素在一行居中，那么将这些元素设置`display:inline-block`，在父元素设置`text-align:center`，或者使用`display: flex; justify-content: center`，实现效果相同，学习后补充解释。如果是多个元素不在一行居中，那么按照 __2__ 的步骤分别设置元素

## 垂直居中

1. 如果是`inline`或`inline-*`

    * 元素为一行
        将元素的上下`padding`设置相同可以是元素内容垂直居中，如果这种方法无效的话，可以设置`height: 100px; line-height: 100px; white-space: nowrap`的属性来使元素垂直居中。即元素的`height`和`line-height`相同，`white-space: nowrap`意思为在元素内不换行。

    * 元素为多行
        将元素上下`padding`设置相同同样作用于多行，如果没有用，那么这个包含内容的元素可能是表格中的单元格或者通过`display: table-cell`属性来使它表现地像一个表格单元格，这种情况我们可以用`vertical-align: middle`来处理，如果这种方法也不行，那么可以使用`flexbox`，一个`flex-child`在`flex-parent`中很容易居中，这样做的前提是父元素有一个固定高度（学习完flex再加以解释），如果这些方法都不行，那么可以使用伪元素占位置，内容与伪元素垂直对齐`vertical-align: middle`

2. 如果是`block-level`元素

    * 已知元素高度

        网页布局中，宽度改变导致文本重新排布会导致高度变化，字体变化会导致高度变化，内容长度改变、图片比例变化都会改变布局的高度。如果高度已知，那么处置居中可以通过`.parent {position: relative;} .child{positoin:absolute; top:50%; height: 100px; margin-top:-50px;}`

    * 未知元素高度

        `.parent {position: relative;}.child {position: absolute;top: 50%;transform: translateY(-50%);}`，`translateY(-50%)`将元素上浮50%

    * 使用`flex`

        `.parent {display: flex;flex-direction:column;justify-content:center;}`，学习完flex后再解释

## 水平垂直居中

> 有时间继续翻译

## Trick

> 在实践中随时补充～