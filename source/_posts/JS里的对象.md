---
title: JS里的对象
date: 2019-03-27 10:00:58
tags:
---

# JS里的对象

## 全局对象window

在浏览器中的全局对象window，标准里的全局对象是global

```javascript
// global
window.parseInt()
window.parseInt()

atob() //将ascii转为Base64字符串
btoa() //将Base64字符串转为ascii

String()
Number()
Boolean()
Object()

window.setTimeout(function(){}, 3000) // 生成一个计时器

// window私有对象（每个浏览器有各自的实现，不统一）
alert() //弹框提示
prompt() //用户填写
confirm() //确认
console //开发者

document //文档 DOM规范（W3C制定）
history //浏览器 BOM规范
```

`new Number()`可以创建一个对象 => `{valueOf(): 1}`会包含很多的API，基本类型是没有属性的，在调用`var n = 1; n.toString()`时，JS会根据`n`的值创建一个临时的`Number`对象，然后获取`toString`的值之后再销毁这个对象

`new String()` 声创建一个对象，是一个字符数组，常用API

```javascript
charAt() //获取某一个索引对应的字符
charCodeAt() //获取某一个索引对应的ascii码
toString(进制) //将数字转换为某个进制
trim() // 去掉字符串两边的空格
concat() // 连接两个字符串
slice(x, y) // 截取x-y中间的字符串
replace(x, y) // 将旧字符串换为新字符串
```

`new Boolean()` 创建了一个对象

`var o1 = {}; o2 = new Object()` 都是对象，但是它们不想等

> 如果函数是window下的，可以不加`window.`的前缀

## 原型链

共用属性：所有对象都需要的一个属性，每个对象都存一个`__proto__`对象，来存储共用属性的值

```javascript
var n = new Number(1)

n.__proto__ // Number对象的共有属性
n.__proto__.__proto__ // Object的共有属性
```

存储共有属性的名字叫做`prototype`，即原型

`var xx = new xxx()` var后面接一个对象，new后面跟一个函数对象（一般的）

> 对象.__proto__ === 函数.prototype //true