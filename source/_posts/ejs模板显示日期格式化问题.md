---
title: 关于ejs模板显示日期格式化问题
subtitle: 
description: 关于ejs模板显示日期格式化问题
author: huier
email: qiuyuhuier@163.com
language: zh-CN
date: 2017-5-28 14:56:58
tags:
- 技术
categories:
- 目录
comments: true
---

# 关于ejs模板显示日期格式化问题

从数据库提取日期,会直接显示为:Sun May 28 2017 16:17:34 GMT+0800 (CST),这样显示对应国内用户非常不友好。得要对日期进行格式化,
但有个问题就是,如果在渲染模板前处理,要每次查询完的就要提取日期然后再进行格式化再赋值回去,这样会显得很麻烦,所以格式化日期得要在ejs的模板渲染时处理

这里时间格式化用的是moment,先加载

var moment = require('moment');

找了相关资料,有三种方式:

1.渲染参数传入moment,比如:
res.render("foo.ejs", { moment: require("moment"), date: date });

模板格式:
<%= moment(date).formate('YYYY-MM-DD HH:mm:ss') %>

这种方法问题: 只要有日期格式的页面,都要导入moment,并传moment,页面多了,这样做很麻烦,并且也不友好。


2.通过ejs的filter方法(过滤器)

```
var moment = require('moment');
var ejs = require('ejs');
ejs.filters.dateformat = function(obj, format) {
    return moment(obj).format('YYYY-MM-DD HH:mm:ss');

};
```

ejs代码：

``` <%=: m.getShowDate | dateformat %> ```


3.通过express的(app.locals)[https://cnodejs.org/topic/5791794a4cddcb43261466cb]设定一个日期格式化方法,贯彻整个程序生命周期,
如果是某个请求可以使用res.locals

utils.js
```
exports.dateFormat = function (date) {
  return moment(date).format('YYYY年MM月DD日hh:mm:ss dddd');
}
```

app.js
```
var app = require('express');
var utils = require('./utils');
app.locals.dateFormat = utils.dateFormat;
```

ejs代码：

``` <%= dateFormat(getShowDate) %> ```

这里推荐3种方法,它只需要开始设置一次就可以,程序就可以任意一处引用。


[参考](https://cnodejs.org/topic/53a3f8fbc3ee0b58204cc72a)
