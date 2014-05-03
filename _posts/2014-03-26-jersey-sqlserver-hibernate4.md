---
layout: post
title: 用Jersey构建RESTful服务6--Jersey+SQLServer+Hibernate4.3
date: 2014-03-26 03:24
author: admin
comments: true
categories: [Java, Jersey, REST]
tags: [Java, Jersey, RESTful]
---
一、总体说明

本例运行演示了用Jersey构建RESTful服务中，如何同过Hibernate将数据持久化进SQLServer的过程

&nbsp;

二、环境

1.上文的项目RestDemo

2.SQLServer2005

三、配置

与上文mysql的配置不同点主要在hibernate.cfg.xml文件；
配置如下：

&nbsp;

&lt;?xml version='1.0' encoding='utf-8'?&gt;
&lt;!DOCTYPE hibernate-configuration PUBLIC
"-//Hibernate/Hibernate Configuration DTD 3.0//EN"
"http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd"&gt;

&lt;hibernate-configuration&gt;
&lt;session-factory&gt;
&lt;!-- Database connection settings --&gt;
&lt;property name="connection.driver_class"&gt;net.sourceforge.jtds.jdbc.Driver&lt;/property&gt;
&lt;property name="connection.url"&gt;jdbc:jtds:sqlserver://192.168.1.10:1433;RestDemo&lt;/property&gt;
&lt;property name="connection.username"&gt;sa&lt;/property&gt;
&lt;property name="connection.password"&gt;aA123456&lt;/property&gt;
&lt;property name="hibernate.default_schema"&gt;RestDemo&lt;/property&gt;
&lt;!-- JDBC connection pool (use the built-in) --&gt;
&lt;property name="connection.pool_size"&gt;1&lt;/property&gt;
&lt;!-- SQL dialect --&gt;
&lt;property name="dialect"&gt;org.hibernate.dialect.SQLServerDialect&lt;/property&gt;
&lt;!-- Enable Hibernate's automatic session context management --&gt;
&lt;property name="current_session_context_class"&gt;thread&lt;/property&gt;
&lt;!-- Disable the second-level cache --&gt;
&lt;property name="cache.provider_class"&gt;org.hibernate.cache.internal.NoCacheProvider&lt;/property&gt;
&lt;!-- Echo all executed SQL to stdout --&gt;
&lt;property name="show_sql"&gt;true&lt;/property&gt;
&lt;!-- Drop and re-create the database schema on startup --&gt;
&lt;property name="hbm2ddl.auto"&gt;update&lt;/property&gt;
&lt;mapping resource="com/waylau/rest/bean/User.hbm.xml"/&gt;
&lt;/session-factory&gt;
&lt;/hibernate-configuration&gt;

四、问题

&nbsp;

可能会出现如下错误

&nbsp;

ERROR: 指定的架构名称 "RestDemo" 不存在，或者您没有使用该名称的权限。
三月 26, 2014 3:38:43 下午 org.hibernate.tool.hbm2ddl.SchemaUpdate execute
INFO: HHH000232: Schema update complete
Hibernate: insert into RestDemo.T_USER (userName, age, USERID) values (?, ?, ?)
三月 26, 2014 3:38:43 下午 org.hibernate.engine.jdbc.spi.SqlExceptionHelper logExceptions
WARN: SQL Error: 208, SQLState: S0002
三月 26, 2014 3:38:43 下午 org.hibernate.engine.jdbc.spi.SqlExceptionHelper logExceptions
ERROR: 对象名 'RestDemo.T_USER' 无效。

解决方案：

&nbsp;

将配置文件中的“hibernate.default_schema”值修改为如下即可：

&lt;property name="hibernate.default_schema"&gt;RestDemo.dbo&lt;/property&gt;

或者去掉上面的配置，在“User.hbm.xml”修改如下

&lt;class name="User" table="T_USER" schema="RestDemo.dbo"&gt;
