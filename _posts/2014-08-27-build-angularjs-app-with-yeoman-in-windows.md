---
layout: post
title: 在Windows环境下用Yeoman构建AngularJS项目
date: 2014-08-27 01:40
author: admin
comments: true
categories: [Yeoman]
tags: [Yeoman,angularjs]
---

本文将通过 Yeoman 创建一个 AngularJS 应用，同时 也能感受到 [Grunt](http://gruntjs.com/) 和 [Bower](http://bower.io/) 的功能。

#认识Yeoman
Yeoman 是一位戴帽子、立意奇颖的人。

通过很少的命令，就能给你整个应用或者独立的模块生成模板代码，比如控制器或者模型。Yeoman可以启动预览Web服务器，观察文件，如果被编辑，就会重新加载的变化和编译你的[Sass](http://www.w3cplus.com/sassguide/)。Yeoman也可以运行单元测试，最小化代码，优化图像等等。

![认识Yeoman](http://yeoman.io/assets/img/codelab/image_1.c942.png)

Yeoman 致力于提高你在构建web应用时的生产力和舒适度，用到三种核心工具：yo（脚手架工具），grunt（构建工具），bower（包管理工具）。

[Yo](http://yeoman.io/) 一个用于构建特定框架的生态系统的代码工具，称之为生成器(generator)。使用 yo 就能提前处理那些些繁琐的任务。

[Grunt](http://gruntjs.com/) 被用来构建，预览以及测试你的项目，感谢来自那些由 Yeoman 团队和 [grunt-contrib](https://github.com/gruntjs/grunt-contrib) 所管理的任务的帮助。

[Bower](http://bower.io/) 被用来进行依赖管理，所以你不再需要手动的下载和管理你的脚本了。

你能使用 [npm](http://npmjs.org/) 安装生成器，现在可用的生成器数量已经超过了 [500个生成器](http://yeoman.io/community-generators.html)，这其中很多都是由开源社区编写的。比较受欢迎的有 [generator-angular](https://github.com/yeoman/generator-angular)、 [generator-backbone](https://github.com/yeoman/generator-backbone)、 [generator-ember](https://github.com/yeoman/generator-ember)。

##为毛用Yeoman
对前端 Web 开发者而言，有这么多伟大的工具存在，但有时很难理解它们是如何结合在一起的。确定了一个工作流，你感到快乐，往往是一个非常个人的努力，但开始并不容易。Yeoman 旨在解决这一问题，用脚手架工作流程创建现代网络应用程序，而在同一时间，许多已演变为行业内的最佳实践的混合。

参考 ：

* [http://yeoman.io/codelab.html](http://yeoman.io/codelab.html)

#设置开发环境
大部分与 Yeoman 相互作用是通过命令行。支持MAC、Linux、Windows。本文以 Windows 为例

##安装前提
安装 Yeoman, 先要安装:

* Node.js v0.10.x+ ：[下载](http://nodejs.org/dist/v0.10.31/x64/node-v0.10.31-x64.msi)
* npm (在 Node 中做了捆绑) v1.4.3+
* git
 
确认安装成功：

	$ node --version && npm --version