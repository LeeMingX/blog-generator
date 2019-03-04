---
title: demo.sh
date: 2019-03-05 01:26:41
tags:
---

### 题目
>
> 1. demo.sh xxx 可在当前目录下生成目录 xxx，demo.sh yyy 可生成目录 yyy
> 2. 如果要生成的目录已经存在，则直接退出
> 3. 生成的目录结构如下：
> ```bash
>├── css
>│   └── style.css
>├── index.html
>└── js
>     └── main.js
> ```
> 4. index.html 的内容为
> ```html
>  <!DOCTYPE>
>  <title>Hello</title>
>  <h1>Hi</h1>
> ```
> 5. css/style.css 的内容为
> ```css
>  h1{color: red;}
> ```
> 6. js/main.js 的内容为
> ```javascript
>  var string = "Hello World"
>  alert(string)
> ```

### 解答过程

```javascript
#! /usr/bin/env node

let fs = require("fs")

dir_name = process.argv[2]

if (fs.existsSync("./" + dir_name)) {
    console.log("ERR: file exists")
    process.exit(1)
} else {
    fs.mkdirSync(dir_name)
    fs.mkdirSync(dir_name + "/css")
    fs.mkdirSync(dir_name + "/js")

    var html_str = "<!DOCTYPE>\n<title>Hello</title>\n<h1>Hi</h1>"
    var css_str = "h1{color: red;}"
    var js_str = "var string = 'Hello World'\nalert(string)"

    fs.writeFileSync(dir_name + "/index.html", html_str)
    fs.writeFileSync(dir_name + "/css/style.css", css_str)
    fs.writeFileSync(dir_name + "/js/main.js", js_str)
}
```

```bash
mv demo.js demo

chmod +x demo

echo "export PATH=$(pwd):$PATH" >> ~/.bashrc

demo xxx
```