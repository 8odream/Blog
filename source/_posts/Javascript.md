---
title: Javascript
date: 2023-10-22 15:36:02
tags:Javascript
---

## 基础内容

### 变量

``` Javascript

```

### 获取元素

``` Javascript
x=doucument.getElementById("element_id");
x=doucument.getElementsByClassName("element_class");

x=doucument.querySelector("element"); ///注意，这种方法可以用前缀#来检索class，用前缀.来检索id
```

### 打印内容

``` Javascript
console.log("content");
```

### 对元素进行修改

```Javascript
x.InnerHTML="content";

x.src="src_link";
x.style.color="color_type";
```

### 匹配元素

```Javascript
x.src.match("content"); ///返回值为String类型的content。支持正则表达式
```

### 在html中写入内容

```Javascript
documente.write("content"); ///注意，如果在文档外链接写入，将会清空原文档内容。尽量在html文档内使用。
```