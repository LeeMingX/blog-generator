---
title: datastructure
date: 2019-03-14 18:10:30
tags:
---

# 数据结构

## 哈希/计数排序

哈希：key-value结构

计数排序：使用hash结构来对数组进行排序

缺点：

1. 需要hash结构
2. 无法处理小数

## 桶排序/基数排序

桶排序：给定一个间隔，每个hash的value为一个间隔长度的数组，对于这个value可以使用其它的排序方法

基数排序：按照进制来划分，则hash的key只有10个，按照个位开始，保证个位从小到大排序，之后每一位都这样处理，value为队列结构

```js
213 33 2953 13 54

213 33 2953 13 54
213 13 33 2953 54
13 33 54 213 2953
```

## 队列和栈

队列：先进先出，js中的Array通过`push`和`shift`方法来实现队列
栈：后进先出，js中的Array通过`push`和`pop`方法来实现栈

## 链表和树

链表是不连续的，删除快，数组增加快

树：层级结构

## 堆排序

堆：子节点小于父节点
最大堆：最大节点要在根结点
最小堆：最小节点在根节点

堆变更：把不是最大堆的结构改为最大堆