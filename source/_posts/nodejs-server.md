---
title: nodejs-server
date: 2019-03-06 20:07:01
tags:
---

# NodeJS Server

## 网络与常用IP

TCP-传输控制协议（transmission control protocol）
IP协议-如何连接的含义

TCP和UDP协议的区别
TCP可靠，面向连接，相对UDP较慢
UDP不可靠，不面向链接，相对TCP较快

三次握手：
客户端：我要连接了
服务端：准备好了，可以连了
客户端：我连接到你了

端口：使用TCP或UDP协议访问一个设备，需要指定端口号(port)

* http服务：80端口
* https服务：443端口
* ftp服务：21端口

0-1023端口是留给系统使用的，管理员权限可以使用

## 一个最简单的Node.js Server

```javascript
var http = require("http")
var fs = require("fs")
var url = require("url")

var port = process.argv[2]

if (!port) {
    console.log("请输入端口号，eg node server 8888")
    process.exit(1)
}

var server = http.createServer(function(request, response){
    var parsedURL = url.parse(request.url, true)
    var pathWithQuery = parsedURL.url
    var queryStr = ""
    if (pathWithQuery.indexOf("?") > 0) {
        queryStr = pathWithQuery.subString(pathWithQuery.indexOf("?"))
    }
    var path = parsedURL.path
    var query = parsedURL.query
    var method = request.method

    console.log("带参数的请求路径：", path)
    console.log("请求参数：", query)
    console.log("请求类型：", method)

})

server.listen(port)
console.log("服务器已启动，正在监听：", port)
```