---
title: DOM事件模型
date: 2019-05-19 18:00:25
tags:
---

# DOM事件模型

## 历史

* DOM1(Core/Html)
* **DOM2(Events)** 广泛应用的
* DOM3

### DOM L1

html中 `<button onclick="y()">xx</button>`，其中 `y()`为要执行的代码，等同于 `eval()`

onclick、onerror、onload、onmouseenter

### DOM L2

`xxx.addEventListener('click', function() {})`

`onclick`只能绑定一个属性

`addEventListener`为一个队列结构，先注册的函数先触发，后进去的后触发

`removeEventListener`删除一个事件函数

所有不同事件函数的队列相互独立

### 重叠元素的事件

```html
<div id="grand">
    爷爷
    <div id="parent">
        父亲
        <div id="child">
            儿子
        </div>
    </div>
</div>
```

1. 点击了儿子，那么同时也点了父亲和爷爷
2. 当三个元素都有绑定事件时，点击儿子时都会触发
3. 嵌套元素中，如果在 `addEventListener`中传递 `True`参数，则从外到内执行，否则从内到外执行，默认从内到外执行

从外到内为捕获过程

从内到外为冒泡过程

这两个过程为事件模型

如果在最内部元素中既加入捕获事件又加入冒泡事件，那么哪个事件先写就先触发哪个