---
title: JS数组
date: 2019-03-31 10:21:05
tags:
---

# JS数组

`String(xxx)`会将传入的内容转为字符串，`new String(xxx)`会将传入的内容转为`String()`对象，除了`Object`以外，其它的标准库函数都是这种行为

`var a = Array(3)`定义了一个长度为3的数组

`var a = Array(3, 3)`定义了一个元素为两个3的数组

`var a = new Array(3)`和上面的行为一致

`var f = function(a, b) { return a + b; }`定义了一个函数

`var f = new Function('a', 'b', 'return a + b')`同样定义了一个函数

## 什么是数组

数组和对象的直接原型是不同的

```javascript
var a = [1, 2, 3]
console.dir(a)

var b = {0: 1, 1: 2, 2: 3, 'length'; 3}
console.dir(b)

// a.__proto__ === Array.prototype true
// b.__proto__ === Array.prototype false
// b.__proto__ === Object.prototype true
// 由于对象和Array的共有属性指向不同，所以a和b不是同一个对象
```

### 伪数组

原型链中没有`Array.prototype`的类似数组数据结构的对象，`arguments`表示传给函数的参数，是一个伪数组

### 数组API

1. foreach

```javascript
var a = [1, 2, 3]

// item是value，index是索引
a.forEach(function(item, index){
    console.log(item, index)
})

// a.forEach(fn) 等价于 a.forEach.call(a, fn)

a.sort(function(x,y) {
    return x - y
})
//排序的结果，x-y。结果为-1，小数在前，y-x，结果为1，小数在后，x-y，结果为1，大数在后。y-x，结果为-1，大数在前

a = [1, 2, 3]
a.join('bug')
// 1bug2bug3 数组变字符串 等价于 a+''
// 如果join不传参数默认传 ','

var a = [1, 2]
var b = [2, 3]
a.concat(b) // [1, 2, 2, 3]
var c = a.concat([]) // 复制一个数组，因为concat会返回一个新数组

var a = [1, 2, 3]
var c = a.map(function(item, index) {
    return item * 2
}) // map返回的结果也是一个列表
var c = a.map(value => value * 2)

var a = [1, 2, 3]
var b = a.filter(function(item, index) {
    if (item > 1) {
        return true
    } else {
        return false
    }
}) // 返回的值是一个列表

a.filter(fn1).map(fn2) // 函数的链式操作，因为它们中间返回的数据类型都是相同的

var a = [1, 2, 3]
var b = a.reduce(function(last, n) {
    return last + n
}, 1) // 规约, 第二个参数是初始值，第一个参数为计算函数，函数的第一个参数是上一个结果，第二个参数是当前计算的值
a.reduce((sum, n) => sum + n, 0)
```