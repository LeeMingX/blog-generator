---
title: new-with-html
date: 2019-03-05 22:41:42
tags:
---

# 入门HTTP

历史：email、邮件讨论组、FTP地址下载资源、HTTP和Gopher、HTML只是超级文本之一

## WWW的发明

1. URI：统一资源标识符
2. HTTP
3. HTML：页面跳转

URN-统一资源名称：唯一实体对应的名称
URL-统一资源定位符：唯一确定网页位置，不确定位置

.com 等：顶级域名
baidu 等：二级域名
www 等：三级域名

锚点：标记文章内跳转的位置

DNS:域名系统  域名 -> ip

* nslookup
* ping

## HTTP

Server: 服务器电脑运行的软件
Client: 电脑运行的浏览器

TCP/IP协议，0～2048端口指定服务

21 FTP 443 https 1080 代理服务器 3306 mysql 80 http

HTTP指导客户端和服务器沟通

`curl -s -v -H "" -- "www.baidu.com"`

```bash
# > 为请求内容， < 为相应内容
> GET / HTTP/1.1
> Host: www.baidu.com
> User-Agent: curl/7.54.0
> Accept: */*
> Lee: xxx
>
< HTTP/1.1 200 OK
< Accept-Ranges: bytes
< Cache-Control: private, no-cache, no-store, proxy-revalidate, no-transform
< Connection: Keep-Alive
< Content-Length: 2381
< Content-Type: text/html
< Date: Tue, 05 Mar 2019 15:16:02 GMT
< Etag: "588604fc-94d"
< Last-Modified: Mon, 23 Jan 2017 13:28:28 GMT
< Pragma: no-cache
< Server: bfe/1.0.8.18
```

`curl -X post -s -v -H "" -- "www.baidu.com"`

`curl -X post -d "hello" -s -v -H "" -- "www.baidu.com"`

# 请求的格式

1. 动词 路径 协议/版本
2. key : value
3. 回车 -> 区分第二部分和第四部分
4. 数据

GET：获取
POST：上传
PUT、PATCH：整体更新、部分更新
DELETE：删除
HEAD、OPTIONS

路径包含查询操作，不包括锚点

content-type标明数据格式
最常见的格式`application/x-www-form-urlencoded`

x-表示还没有写入规范，使用url编码

# 响应的格式

1. 协议/版本
2. key : value（Content-Length,Content-Type）
3. 回车
4. 返回数据

状态码：服务器对浏览器说的话

* 1xx 不常用
* 2xx 200(get) 204(post)
* 3xx 滚 301(永久不存在) 302(暂时不存在) 304(和上次返回相同)
* 4xx 请求端出错 404
* 5xx 服务器出错 502 500

> Content-Type遵循MIME规范