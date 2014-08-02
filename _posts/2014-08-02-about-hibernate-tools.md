---
layout: post
title: Hibernate tools介绍、安装、使用
date: 2014-08-02 01:40
author: admin
comments: true
categories: [Hibernate]
tags: [Hibernate]
---

#介绍
[http://hibernate.org/tools/](http://hibernate.org/tools/)

#版本
[http://tools.jboss.org/downloads/overview.html](http://tools.jboss.org/downloads/overview.html)

选择对应的版本
`Eclipse Luna 4.4`的最新版本是 `JBoss Tools 4.2.0.Beta3`

##下载
下载安装方式有如下三种：
##1.从marketplace
[http://tools.jboss.org/downloads/jbosstools/luna/4.2.0.Beta3.html#marketplace](http://tools.jboss.org/downloads/jbosstools/luna/4.2.0.Beta3.html#marketplace)

##2.URL站点更新
[http://tools.jboss.org/downloads/jbosstools/luna/4.2.0.Beta3.html#update_site](http://tools.jboss.org/downloads/jbosstools/luna/4.2.0.Beta3.html#update_site)

##3.插件下载
[http://tools.jboss.org/downloads/jbosstools/luna/4.2.0.Beta3.html#zips](http://tools.jboss.org/downloads/jbosstools/luna/4.2.0.Beta3.html#zips)

#参考文档

[https://docs.jboss.org/tools/4.1.0.Final/en/hibernatetools/html_single/index.html](https://docs.jboss.org/tools/4.1.0.Final/en/hibernatetools/html_single/index.html)


#错误解决
 
	Problems while reading database schema
	
	org.hibernate.HibernateException: could not instantiate RegionFactory 

换个项目没有问题。jar 冲突。换不了jar 就再另外一个项目里面把bean ,xml 给生成完了再把代码移回原项目
