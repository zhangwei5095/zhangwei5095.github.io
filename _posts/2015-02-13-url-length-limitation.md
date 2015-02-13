---
layout: post
title: 突破 URL 传值限制 
date: 2015-02-13 01:41
author: admin
comments: true
categories: [Web]
tags: [URL]
---

##问题

window.location = url 方法 当传值url 太长时，服务器无法正常接收。

比如下面，当rowsData 数据量过大时，服务器请求失败。

	window.location='rest/files/excel/easyui-datagird?fileName=' + fileName + '&columns='+columns2+'&rowsData='+rowsData;

##原因

使用浏览器发送 GET 请求会受浏览器 URL 长度的限制。而 window.location.href 就是 GET 请求。

下面数据是从网上找的，不一定准确，但也能了解个大概：

* IE 浏览器对 URL 的最大限制为2083个字符
* Firefox 浏览器 URL 的长度限制为65,536个字符
* Safari URL 最大长度限制为 80,000个字符
* Opera URL 最大长度限制为190,000个字符
* Chrome URL 最大长度限制为8182个字符

##解决办法

将URL地址缩减到浏览器和服务器都可接收的或者换成 POST 请求。

POST理论上是不限制传输数据的。

##参考：

* <http://support2.microsoft.com/default.aspx?scid=kb;EN-US;q208427>