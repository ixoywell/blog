---
title: Markdown语法说明
subtitle: 
description: 
author: huier
email: qiuyuhuier@163.com
date: 2016-5-19 14:56:58
type: "categories"
comments: true
tags:
- 生活
categories:
- 目录

---

Markdown 是一种用来写作的轻量级「标记语言」，它用简洁的语法代替排版，而不像一般我们用的字处理软件 Word 或 Pages 有大量的排版、字体设置。它使我们专心于码字，用「标记」语法，来代替常见的排版格式。


## Markdown语法说明

### 使用 Markdown 的优点

    1.专注你的文字内容而不是排版样式。
    2.轻松的导出 HTML、PDF 和本身的 .md 文件。
    3.纯文本内容，兼容所有的文本编辑器与字处理软件。
    4.可读，直观。适合所有人的写作语言。

### 标题

# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
大标题
=
小标题
-

### 粗体、斜体

**粗体**
__粗体__
*斜体*
_斜体_

### 删除线

删除线的使用，只要用~~将需要删除的文本包围起来即可。

~~Mistaken text.~~


### 代码块高亮

使用\```（三个反引号）包围代码块即可，里面的代码块不需要任何缩进。这种方式也称“围栏式代码块”，如下：

``` bash
$ hexo server
```

More info: [Server](https://hexo.io/docs/server.html)

### Generate static files

``` bash
$ hexo generate
```

More info: [Generating](https://hexo.io/docs/generating.html)

### Deploy to remote sites

``` bash
$ hexo deploy
```

More info: [Deployment](https://hexo.io/docs/deployment.html)
