---
title: JS里的数据类型
date: 2019-03-26 10:45:23
tags:
---

# JS 的数据类型

## 黑历史

- 1991 李爵士发明万维网
- 1992 李爵士的同事发明 CSS
- 1993 W3C 创立
- 1995 网景浏览器，Branden Eich 设计 Mocha 脚本语言（JavaScript）
- unicode、utf-8 发布，JS 不支持此字符集
- 1996 IE 浏览器，JScript
- 网景浏览器开源 Firefox
- 网景向 ECMA 申报 JS 标准（ECMAScript）
- IE5.5 MS 推出 JS 发请求
- 2004 Gmail，网页上的程序，向编程语言的蜕变
- 前端 front-end 概念，2010 年左右在国内有概念
- JS 的缺点：全局变量（没有模块的概念），标准库缺失（ES3 标准）
- ECMA5 升级，增加很多新特性
- Rails 社区发明 CoffeeScript，JS 改良版（类、箭头函数、optional chain 语法）
- ECMAScript6 的升级，JS 成为现代编程语言
- JS 每年一更，ES7 更新了两个特性，ES8 更新新特性，ESNext+Webpack 使用未来的特性

## 数据类型

JS 有 7 种数据类型

1. 数字 Number
2. 字符串 String
3. 布尔值 Boolean
4. Symbol
5. null
6. undefined
7. object

> Array/function 不是数据类型

### number

`.1`和`0.1`等价

二进制->`0b11` 八进制->`0o12` 十六进制->`0xff`

### string

使用`''`或者`""`引起来的字符串

引号中没有自负的字符串是空字符串，只有空格的字符串叫做空格字符串

转义符`\`，双引号里面的单引号或相反是可以的，`\n \t \r \b`等，这些字符的长度是 1

多行字符串，在字符串中使用`\`来分隔多行字符串，使用`+`来组合两个字符串，最好使用后面的方法，ES6 中的 **`** 可以写多行字符串，但是这个字符串是包括回车的

### bool

`true/false`，`&&/||`运算的特点为同真为真，同假为假

`&&`，如果第一个值为`false`，那么返回第一个**值**，否则返回第二个**值**

`||`，如果第一个值为`true`，那么返回第一个**值**，否则返回第二个**值**

### Symbol

表示一个唯一的值

### null、undefined

一个值，是 null

一个值，是 undefined

> null 和 undefined 的区别，如果变量没有值，使用 undefined，如果又一个对象，且不想直接赋值，可以给 null，如果有一个不直接赋值的非对象，可以赋值为 undefined（惯例）

### object

object/hash，由简单类型组成的复杂类型，key-value 结构

```javascript
var person = {
  name: "mouse",
  age: 12
};
person["name"]; // mouse
person.name; // mouse

// person.name 不一定等于 person['name']，因为name可能在别的地方定义过
```

object 中还可以存在 object，key 只能是字符串，如果 key 不加引号，就必须依照标识符的命名规则

`delete person['name']` 可以删除某个 key

`'name' in person //false.` 没有 key

`for(var k in person) { console.log(person[k]) }` 使用`for-in`来遍历对象的 key

使用`typeof`来查看某个变量的类型，类型都是字符串类型，`typeof null // “object”` 属于 bug，`typeof function // "function"` 属于 bug

