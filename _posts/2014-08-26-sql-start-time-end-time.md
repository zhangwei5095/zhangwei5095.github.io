---
layout: post
title: SQL Server取开始时间、截止时间
date: 2014-08-26 01:40
author: admin
comments: true
categories: [SQLServer]
tags: [SQLServer]
---
 
	--当天开始
	SELECT dateadd(ms,0,DATEADD(dd, DATEDIFF(dd,0,getdate()), 0))		  当天开始
	--当天结束
	SELECT dateadd(ms,-3,DATEADD(dd, DATEDIFF(dd,-1,getdate()), 0))		  当天结束
	
	--当月第一天
	SELECT DATEADD(mm, DATEDIFF(mm,0,getdate()), 0)						  当月第一天
	--当月最后一天
	SELECT   dateadd(ms,-3,DATEADD(mm,   DATEDIFF(m,0,getdate())+1,   0)) 当月最后一天
