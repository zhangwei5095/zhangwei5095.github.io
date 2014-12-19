---
layout: post
title: SVN 服务器安装
date: 2014-12-20 01:21
author: admin
comments: true
categories: [SVN]
tags: [SVN]
---

VisualSVN Server 3.2.2 (Apache Subversion 1.8.11)

Apache Subversion 1.8.11 发布说明

http://mail-archives.apache.org/mod_mbox/subversion-dev/201412.mbox/
%3C548F4EF1.9070900@apache.org%3E

Apache Subversion 1.8.x 兼容性说明
http://subversion.apache.org/docs/release-notes/1.8.html

兼容性问题

旧客户端和服务器与 1.8 服务器和客户端互操作是透明的。然而,1.8 的一些新特性可能
不可用,除非客户端和服务器都是最新版本。还有另外的情况下,当客户端是新的，服务器
是旧的，新功能可以用但运行可能比较低效。

不需要转储和重新加载您的存储库。Subversion 1.8 服务器可以读取和写入由早期版本创
建的存储库。升级现有的服务器，仅需安装最新的库和二进制文件到旧的上面。

Subversion 1.8保持与较早版本的 API/ABI 兼容性,仅添加新功能,从来没有删除旧的。一
个程序写入任何以前 1.x 版本的 API都可以编译和运行使用 1.8 的库。然而,给 1.8 编
写的程序不能编译或运行在旧的库上。

有可能在有限的情况下，旧的行为的API从以前的版本中已略作修改。在这些情况下，功能
的边缘情况，被认为是错误，并因此改善或消除。请查阅API勘误表
(http://svn.apache.org/repos/asf/subversion/trunk/notes/api-errata/1.8/)上的这
些API，获取这些变化可能有什么影响的更详细的信息。
---------------------------
visualsvn

下载说明
https://www.visualsvn.com/server/

带管理界面。服务器免费，客户端收费。包含 Apache Subversion 1.8.11

最新版本 3.2
配置要求 

System Requirements
Operating Systems
Windows Server 2008 or later
Windows Vista or later
Minimum hardware
1.4 GHz CPU

不采用，因为配置不够

----------------------------
win32svn

http://alagazam.net/

Should work (but not tested) on all flavours of Windows
from Win2000 to Win8 including server variants.
(1.7.x does not work on NT4 due to APR using new functions).
512 MB RAM
50 MB hard drive space

只有svn的内核，没有界面，目前最新为 1.8.10。无需注册

------------------------------
sliksvn

https://sliksvn.com

只有客户端下载。sever 是云服务器

--------------------------

wandisco

http://www.wandisco.com/subversion/download


目前 svn 最新为 1.8.10 ，需要注册。客户端 smartSvn收费

------------------------

collabnet

http://www.collabnet.cn/downloads/subversion


功能选择比较多，是 svn 的创始者。没有界面。目前 svn 最新为 1.8.10。需要注册


------------------

最后服务器选了 win32svn   1.8.10
客户端选 tortoisesvn 1.8.10

安装目录
C:\Program Files\Subversion

工作目录
E:\svn

建立版本库（Repository） 

svnadmin create E:\svn\repository，注：这里svn文件夹要先建立好。 

配置用户和权限 

svnserve.conf文件

打开E:\svn\repository, 你会发现已经多了一些目录和文件, 打开conf子目录, 打开
svnserve.conf文件, 这里行前凡是有#的都等于是被注释忽略了, 你可以把#去掉让那一行
生效, 或者自己新添加行. 里面的英文注释已经详细说明了各种设置的含义, 最后你设置 
[general]小节中行前没有#号的内容为: 

anon-access = read
auth-access = write 
password-db = passwd 
authz-db = authz

passwd 文件 

同样, 设置[users]小节中行前没有#号的内容, 例如: 

lww = 123

含义是: 

用户lww的密码为123 


配置 authz文件

授权

启动svn服务


