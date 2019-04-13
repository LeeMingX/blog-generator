---
title: 自己的jQuery
date: 2019-04-13 14:04:44
tags:
---

# 实现自己的 jQuery

## 实现步骤

1. 封装方法
2. 一个命名空间
3. 使用`node.func`的方法来访问
4. 扩展方法
5. 使用真正的 jQuery

## 封装方法

```javascript
// 要封装两个方法 getSiblings 和 addClass
// getSiblings获取某个元素的兄弟节点
// addClass向某个元素添加或删除类名

function getSiblings(node) {
  let all = node.parentNode.children;
  let result = { length: 0 };
  for (let i = 0; i < all.length; ++i) {
    if (all[i] !== node) {
      result[result.length++] = all[i];
    }
  }
  return result;
}

function addClass(node, cl) {
  for (let key in cl) {
    if (cl[key]) {
      node.classList.add(key);
    } else {
      node.classList.remove(key);
    }
  }
}

// addClass方法中对classList的增减操作可以简化，因为它只和传入的类名的true或false有关
function addClassPro(node, cl) {
  for (let key in cl) {
    let methodname = cl[key] ? "add" : "remove";
    node.classList[methodname](key);
  }
}
```

## 一个命名空间

为了防止封装的函数可能会将一些全局变量覆盖掉，可以定义一个统一的命名空间

```javascript
let mouse = {};
mouse.getSiblings = getSiblings;
mouse.addClass = addClass;

// usage
mouse.getSiblings(node);
mouse.addClass(node, { class1: true });
```

## 使用`node.func`的方法来访问

第一种方法可以在`Node.prototype`原型链上直接将我们封装的方法写进公有属性，这种方法比较简单，但是我们有时不需要所有的 Node 对象都具有某些属性，所以我们采用第二种方法

第二种方法是定义一个函数，它接收一个 DOM 元素，并返回一个拥有我们的封装函数的对象

```javascript
let mouse = function(nodeOrString) {
  let nodes = { length: 0 };
  switch (typeof nodeOrString) {
    case "string":
      nodes = document.querySelectorAll(nodeOrString);
      break;
    case "object":
      nodes[nodes.length++] = nodeOrString;
      break;
    default:
      break;
  }
  return {
    getSiblings: function() {
      return "";
    },
    addClass: function(cl) {
      return;
    }
  };
};
```

## 扩展方法

使用上述方法可以在返回的对象中扩展任何 DOM 中没有提供的 API

## 真正的 jQuery

实际上 jQuery 并没有使用上述方法来实现，其使用了原型链的相关知识，但是使用的过程和上述结果相同，在应用中需要慢慢积累
