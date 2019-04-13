---
title: JS函数
date: 2019-04-01 21:29:39
tags:
---

# JS 函数

## 函数的 5 种声明

### 具名函数

```javascript
function x(input1, input2) {
  return undefined;
}
```

> 浏览器中的 console.log(xxx)，返回值为 undefined

### 匿名函数

```javascript
var x = function(input1, input2) {
  return;
};
```

### 给变量赋值一个具名函数

```javascript
var x = function y(input1, input2)
// console.log(y) -> undefined
// y的作用域只在这个y函数内部
```

### window.Function

```javascript
new Function("input1", "input2", "return input1 + input2");
```

### 箭头函数

```javascript
(input1, input2) => input1 + input2

(input1, input2) => {
    var x = input1 + input2
    return x
}

input1 => input1 ** 2
```

> 所有的函数都有一个属性叫做`name`，匿名函数的名字为变量名，将具名函数赋值给一个变量，调用这个变量的`f.name`会显示具名函数的名称，使用`new Function()`以后这个函数的名字叫`anonymous`

## 如何调用函数

```javascript
function f(x, y) {
  return x + y;
}

Function.prototype = {
  call: function() {},
  apply: function() {},
  bind: function() {}
};

// 调用函数（函数是可以反复调用的代码块）
// Function的call方法，这个方法实质上是调用eval(函数题)
// f是这个函数对象
// f.call()是调用函数
// 可以执行代码的对象是函数
f.call(undefined, 1, 2); // 3
```

`eval(xxx) //将字符串识别为代码识别`

## 什么是 call stack

```javascript
function a() {
  console.log("a");
  return "a";
}

function b() {
  console.log("b");
  return "b";
}

function c() {
  console.log("c");
  return "c";
}

a.call();
b.call();
c.call();
// 调用方法从上到下，调用完一个之后会删除

function a() {
  console.log("a");
  b.call();
  return "a";
}

function b() {
  console.log("b");
  c.call();
  return "b";
}

function c() {
  console.log("c");
  a.call();
  return "c";
}

a.call();

// call stack过程
// a.call()
// console.log("a")
// b.call()
// console.log("b")
// c.call()
// console.log("c")
// return c
// return b
// return a
```

递归调用

`stackoverflow`: 栈空间溢出

## this 和 arguments

```javascript
f.call(undefined, 1, 2);
// undefined => thih, [1, 2] => arguments
```

1. call 的第一个参数可以用 this 得到
2. call 的后面参数可以用 arguments 得到

> 在浏览器中，在调用 call 时，如果不是严格模式，this 为 window 对象，如果使用严格模式，会打印出传入的值
>
> arguments 是伪数组，原因是在原型链中没有 Array.prototype

## 作用域

```javascript
var a = 1;
function f1() {
  var a = 2;
  f2.call();

  function f2() {
    var a = 3;
    console.log(a);
  }
}

f1.call();
console.log(a);

//全局作用域（a, f1）+child（f1）
//f1作用域 （a, f2）+child（f2）
//f2作用域 （a）
//就近原则找作用域
//作用域内变量提升（声明在头部）
```

## 闭包

如果一个函数使用了他范围外的值，那么（这个函数+这个变量）就叫做闭包
