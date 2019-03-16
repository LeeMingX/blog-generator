---
title: http-css-summary
date: 2019-03-11 19:11:05
tags:
---

# 复习

## http入门

```batch
# GET请求

GET / http/1.1
Host: baidu.com
Accept: text/html

# GET响应

http/1.1 200 OK
Content-type: text/html; charset=utf-8
Content-length: 10000

<!DOCTYPE html>
<html></html>

# POST请求

POST / http/1.1
Host: baidu.com
Accept: application/json
Content-type: text/-x-www-form-urlencoded
Content-length: 100

username=d&password=i

# POST响应

http/1.1 403 Forbidden
Content-type: application/json
Content-length: 100

{"error": "hello?"}
```

### 调试工具

chrome的调试工具中的Network模块为http请求响应调试工具

## HTML

html页面上的`<meta charset="utf-8">`在后台指定好字符集时可以省略，协议的字符集大于内容的字符集

`<meta name="author" content="laowu">`可以指定页面作者

seo优化，可以添加`<meta name="keyword" content="前端开发">`

对文档的描述可以添加`<meta name="description" content="这就是前端">`

html示例页面

```html
<body>
    <h1>Hello world</h1>
    <a href="javascript:;" target="_blank">papa</a>
    <form action="./login" method="post">
        <label>用户名：<input type="text" name="username"></label>
        <input type="submit" value="提交">
    </form>
</body>
```

## CSS

1. float + clearfix

    ```css
    .clearfix {
        content: "";
        display: block;
        clear: both;
    }
    ```

2. 高度是由什么决定的
div的高度由文档流里面的元素高度的总和决定的，span由行高决定的

    > webpage free psd 下载免费的psd（photoshop支持的）文件，然后再使用图片

3. 用padding还是用margin
哪个能实现用哪个，padding+border-box使用很好用

4. href一般是外部文档，src一般是内部资源
