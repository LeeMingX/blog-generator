---
title: html
date: 2019-03-07 16:04:44
tags:
---

# HTML

## 买个域名

用于发布网站

## 写一个简历

简历：内容+外观

> 需要用什么学什么

1. 必须写
    1. 个人信息：姓名，性别，年龄，学校，所在城市，目标职位，不    写目标薪资
    2. 教育经历
    3. 工作经历：有经验就写
    4. 项目经验：4-6个项目内容

2. 可选部分：
    1. 开源代码
    2. 博客链接
    3. 外文翻译
    4. 他人评价
    5. 自拍
    6. 对公司业务的分析

## HTML简介（超文本标记语言）

1. HTML的版本
    1. HTML 4.01
    2. XHTML
    3. HTML5 （*最通用,兼容旧版本语言，能在微信上显示的网页统称h5）
    4. HTML5.1
2. 规范文档（W3C）：根据实际情况总结
3. DOCTYPE
    1. 用来选择文档类型
4. html head body标签都可以省略，title标签不能省略
5. 常见标签：a form input button h1-h6 p ul ol smallstrong div(divide) span(span,行级划分) kbd(keyboard，表示键盘上的按键) video audio svg(不规则图形)
6. 除了div和span，其它标签都有默认样式
7. 查看MDN上的文档

> html中没有块级元素和内联元素的区别，css中有区别

## 课后作业

1. W3C 简介（查维基百科）
The W3C also engages in education and outreach, develops software and serves as an open forum for discussion about the Web.
W3C是（全称是World Wide Web Consortium 万维网联盟）为WWW万维网指定国际标准的组织，由李爵士（Tim Berners-Lee）创建，由很多全职员工组成，他们的工作是对万维网的发展来制定标准，截止2018.11.19，该组织已经由476名成员。W3C同时也致力于Web方面的教育和软件开发，以及服务于开放论坛
2. MDN 简介（查维基百科）
MDN（全称是Mozilla Developer Network/原称Mozilla Developer Center），是Mozilla对于web标准和Mozilla项目的官方开发文档网站
MDN是开发者的资源，由开发者社区和技术作者以及其它网络上不同主题的文档（HTML5，JavaScript，CSS，Web APIs，Node.js，WebExtensions，MathML）来维护，对于移动端web开发者，MDN提供了像开发HTML5移动端app和移动端插件、位置感知app的文档
3. HTML 所有标签列表（查 MDN）

```html
<a>
<!-- <a>标签创建了一个超链接到其它的网页，文件，或者同一网页的各种位置，邮箱地址或者其它url -->
<abbr>The HTML Abbreviation element (<abbr>) 
<!-- <abbr>标签表示缩写或首字母缩略字，有可选的title属性，对缩写提供一个扩展或描述，如果出现了这个标签，那么title必须包括全部解释并且没有其它元素 -->
<address>
<!-- <address>标签代表该HTML提供的某人或某个组织的联系信息 -->
<area>
<!-- <area>标签代表了一张图上的热点区域，可选属性关联到某个链接，这个标签只在<map>中使用 -->
<article>
<!-- <article>标签代表文档、页面、应用、站点中的独立组件，可以单独分配或重用 -->
<aside>
<!-- <aside>元素代表文档中和主要内容无关的一部分，经常被用于侧边栏或标注框中 -->
<audio>
<!-- <audio>标签用于内嵌声音内容到页面，可能包括一个或多个音源，使用src属性或<source>标签，浏览器会选择更合适的。也可以是流媒体的位置，使用MediaStream -->
<b>
<base>
<basefont>
<bdi>
<bdo>
<bgsound>
<big>
<blink>
<blockquote>
<body>
<br>
<button>
<canvas>
<caption>
<center>
<cite>
<code>
<col>
<colgroup>
<command>
<content>
<data>
<datalist>
<dd>
<del>
<details>
<dfn>
<dialog>
<dir>
<div>
<dl>
<dt>
<element>
<em>
<embed>
<fieldset>
<figcaption>
<figure>
<font>
<footer>
<form>
<frame>
<frameset>
<h1>
<head>
<header>
<hgroup>
<hr>
<html>
<i>
<iframe>
<image>
<img>
<input>
<ins>
<isindex>
<kbd>
<keygen>
<label>
<legend>
<li>
<link>
<listing>
<main>
<map>
<mark>
<marquee>
<menu>
<menuitem>
<meta>
<meter>
<multicol>
<nav>
<nextid>
<nobr>
<noembed>
<noframes>
<noscript>
<object>
<ol>
<optgroup>
<option>
<output>
<p>
<param>
<picture>
<plaintext>
<pre>
<progress>
<q>
<rb>
<rp>
<rt>
<rtc>
<ruby>
<s>
<samp>
<script>
<section>
<select>
<shadow>
<slot>
<small>
<source>
<spacer>
<span>
<strike>
<strong>
<style>
<sub>
<summary>
<sup>
<table>
<tbody>
<td>
<template>
<textarea>
<tfoot>
<th>
<thead>
<time>
<title>
<tr>
<track>
<tt>
<u>
<ul>
<var>
<video>
<wbr>
<xmp>
```

4. 什么是空标签（查 MDN、博客）
没有内容的HTML元素叫做空元素/空标签，例如`<br>`是一个没有结束符的空元素，空元素可以通过`<br />`被“关闭”，HTML5不需要空元素必须关闭
5. 什么是可替换标签（查 MDN、博客）
这些元素是一种外部对象，它们外观的渲染是独立于CSS的，它们的内容不受当前文档的样式影响，CSS可以影响可替换元素的位置，但不会影响可替换元素自身的内容，某些可替换元素，例如`<iframe>`元素可能具有自己的样式表，并且不会继承父文档的样式

典型的可替换元素包括：

* `<iframe>`
* `<video>`
* `<embed>`
* `<img>`

有些元素仅在特定情况下被作为可替换元素处理

* `<option>`
* `<audio>`
* `<canvas>`
* `<object>`
* `<applet>`

`<input>`元素可替换，因为image类型的input就像`<img>`一样被替换，但其它形式的控制元素，包括其它类型的`<input>`元素，被明确地列为非可替换元素