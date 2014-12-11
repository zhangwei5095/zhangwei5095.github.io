---
layout: post
title: 用 Github、Markdown 和 GitBook 写开源书
date: 2014-12-11 01:41
author: admin
comments: true
categories: [Github,GitBook]
tags: [Github,Markdown,GitBook]
---

之前一直是在 Github 上写开源书（见：[http://www.waylau.com/books/](http://www.waylau.com/books/)）但，由于 Github 本身的目录结构并不一定符合阅读的习惯，而且没有提供 pdf , ePUB, MOBI 等格式的转换下载。很多同学也还是习惯离线看文档。GitBook 就是解决这一问题。

GitBook 让你在保持在 Github 的书写习惯外，稍加配置，就能自动发布到GitBook 上，形成界面漂亮的电子书了（支持 html, pdf , ePUB, MOBI 等）。

##安装

	$ npm install gitbook -g

##初始化项目结构

在项目根目录下创建 SUMMARY.md 文件,如下：
	
	# Summary
	
	This is the summary of my book.
	
	* [section 1](section1/README.md)
	    * [example 1](section1/example1.md)
	    * [example 2](section1/example2.md)
	* [section 2](section2/README.md)
	    * [example 1](section2/example1.md)

执行初始化命令

	$ gitbook init

则自动生成上述文档中的目录组织结构

##修改 md 文件内容，编译

	$ gitbook build ./

![](http://99btgc01.info/uploads/2014/12/02%282%29.jpg)

编译成功，会生成一个 `_book` 目录，里面就是生产的 html 文件。

![](http://99btgc01.info/uploads/2014/12/03%282%29.jpg)

打开该目录，右键运行 index.html 即可看到 gitbook 的效果

![](http://99btgc01.info/uploads/2014/12/04%282%29.jpg)

#1.注册账户

需要拥有 [Github](https://github.com) 和 [GitBook](https://www.gitbook.com) 的账户

#2.关联账号

将 GitBook 关联上  Github 的账号

