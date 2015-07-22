---
layout: post
title: Windows 下 MySQL 简单定时自动备份
date: 2015-07-22 01:08
author: admin
comments: true
categories: [MySQL]
tags: [MySQL]
---

## 问题

MySQL Workbench 客户端虽然好用，但并不提供自动备份功能。手工备份，确实繁琐。

<!-- more -->

## 环境

- Windows 7
- MySQL 5.6.24

## 思考

MySQL 提供了 mysqldump 来进行备份。那么我们可否使用该工具，结合Windows 的定时任务功能，来实现 MySQL 定时自动备份呢？

## 解决

新建一个 数据库备份文件存放目录，本例为`D:\db_backup`新建一个批处理文件，可以起任意名，本例为 `mysql_backup_tool.bat` ，文件内容如下：

	@echo off
	
	set "Ymd=%date:~,4%%date:~5,2%%date:~8,2%"
	C:\mysql\bin\mysqldump --opt --single-transaction=TRUE   --user=root  --password=123456 --host=127.0.0.1 --protocol=tcp --port=3306 --default-character-set=utf8 --single-transaction=TRUE --routines --events "emsc" > D:\db_backup\emsc_backup_%Ymd%.sql
	
	@echo on

其中,`C:\mysql\bin\mysqldump` 为 MySQL 安装时，`mysqldump.exe` 文件所在路径，`--user=root` 指 MySQL 用户名为 `root`  `--password=123456` 指 MySQL 密码为`123456`,`"emsc"` 为要备份的数据库的名称,`emsc_backup_%Ymd%.sql`， 为备份文件的名称，这个名称是根据当前的时间规则生成的，比如今天生产的备份文件，名称为`emsc_backup_20150722.sql` 。

## 定期任务

## 参考
- <http://dev.mysql.com/doc/mysql-backup-excerpt/5.7/en/backup-and-recovery.html>


