---
title: JS深入类型
date: 2019-03-26 13:47:44
tags:
---

# JS的数据类型

## 类型转换

||number|string|boolean|symbol|null|undefined|object|
|-|-|-|-|-|-|-|-|
|number|-|toString|Boolean()|||||
|string|Number()/parseInt(x, 10/2/8)/parseFloat(x.xx)/x-0/+x(--x)|-|Boolean()|||||
|boolean||toString|-|||||
|symbol||||-||||
|null||报错|Boolean()||-|||
|undefined||报错|Boolean()|||-||
|object||[object Object]|Boolean()/值为true||||-|

数字、字符串和对象变成字符串可以通过加一个`''`字符串变成字符串，null和undefined也可以构成字符串，加法运算中，如果运算的值并不都是数字，它们会优先转为字符串

`window.String(xxx)`可以将`xxx`转变为字符串

`Boolean(xxx)`可以将`xxx`转为布尔值，只要是对象，就是true。通过`!!xxx`的方法也可以将任何内容转换为布尔值，number里`0、NaN`，`''`字符串，`undefined`、`null`这五个特殊值为false（**falsy**）

`parseInt(xxx, 2)`函数会从头截取字符串中的有效数字

## 内存图

代码区：存代码
数据区：存数据

数据区：栈内存，堆内存

```javascript
var a = 1
var t = 2
t = a
var o = {'a': 1, 'b': 2}
var o2 = {'c': 4}
o2 = o
var c = true
o.gender = 't'
```

1. 上面的代码先进行变量提升
2. 代码区创建a变量，栈内存中存一个1
3. 代码区创建t变量，栈内存中存一个2
4. 把a的值覆盖掉t的值
5. 栈内存中存一个o的地址，堆内存中存o的内容
6. 栈内存中存一个o2的地址，堆内存中存o2的内容
7. 把o的地址赋值给o2

## 循环引用

```javascript
var a = {}
a.self = a
a.self.self = a
...
```

a对象的self保存的是a本身的地址，上述代码只生成了一个对象

面试题：

```javascript
var a = {n:1}
var b = a
a.x = a = {n:2}
1     2

alert(a.x) //1a和2a开始计算时都为{n:1}，在2a变为{n:2}时，1a还没有变，计算完成后a变为2a，则a.x为undefined
alert(b.x) //b保存的是1a的值，那么b.x为{n:2}
```

## 垃圾回收

> 如果一个对象没有被引用，它就变成了垃圾，将会被回收

```javascript
var a = {name: 'a'}
var b = {name: 'b'}
a = b //a之前引用的对象变成了垃圾
```

```javascript
var fn = function(){}
document.body.onclick = fn
fn = null //由于fn之前引用的函数已经被body引用，所以fn之前引用的不是垃圾
document.body.onclick = null //function(){}会变成垃圾
```

```javascript
var fn = function(){}
document.body.onclick = fn
var fn = null //当页面被关闭后，fn以及它引用的函数变成了垃圾，在IE（6）浏览器中，除非关闭整个浏览器才能关闭，否则不当做垃圾处理
window.onunload = function() {
    document.body.onclick = null // 页面关闭之前把所有事件置为null
}
```

## 深拷贝和浅拷贝

对所有的基本类型，简单的赋值就是深拷贝

对于对象来说：

```javascript
var a = {name='a'}

var b = a
b.name = 'b'
a.name // 'b' 浅拷贝，复制原变量之后，自身改变导致原变量改变

//使用原对象中所有的值创建一个新的对象，然后让另一个变量来引用新的对象，此时完成了对原变量的深拷贝，对于新变量的修改不会影响原变量
```