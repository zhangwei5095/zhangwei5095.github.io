---
layout: post
title: 用Jersey构建RESTful服务7--Jersey+Spring 4
date: 2014-07-25 03:24
author: admin
comments: true
categories: [Java, Jersey, REST]
tags: [Java, Jersey, REST]
---
#一、总体说明

本例运行演示了用Jersey构建RESTful服务中，如何集成Spring4

#二、环境

* 1.上文的项目RestDemo
* 2.Spring:最新稳定版v4.0.6.RELEASE[源码下载](https://github.com/spring-projects/spring-framework/archive/v4.0.6.RELEASE.zip)，
[jar包下载](http://maven.springframework.org/release/org/springframework/spring/4.0.6.RELEASE/spring-framework-4.0.6.RELEASE-dist.zip)。将相关jar包添加进项目


#三、配置

1.根目录下下创建spring的配置文件`applicationContext.xml`；
配置如下：

2.增加 UserService 和 UserServiceImpl

3.修改 UserResource
 
4.修改web.xml,插入

	<module-name>RestDemo</module-name>
	
	<listener>
	  <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
	</listener>
	
	<context-param>
	  <param-name>contextConfigLocation</param-name>
	  <param-value>classpath:applicationContext.xml</param-value>
	</context-param>


**本章源码**：[https://github.com/waylau/RestDemo/tree/master/jersey-demo6-sqlserver-hibernate](https://github.com/waylau/RestDemo/tree/master/jersey-demo6-sqlserver-hibernate)

[https://github.com/waylau/RestDemo/tree/master/jersey-demo6.2-sqlserver-hibernate](https://github.com/waylau/RestDemo/tree/master/jersey-demo6.2-sqlserver-hibernate)