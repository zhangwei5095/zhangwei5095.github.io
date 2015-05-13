---
layout: post
title: CentOS 7 安装、配置
date: 2015-05-12 02:41
author: admin
comments: true
categories: [CentOS]
tags: [CentOS]
---

## 下载

地址：<http://www.centos.org/download/>

本例为 Minimal ISO 版本：<http://isoredirect.centos.org/centos/7/isos/x86_64/CentOS-7-x86_64-Minimal-1503-01.iso>

CentOS 与 RHEL 是同源，所以，在 CentOS 文档不足时，可以参考 RHEL 的文档。<https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/Installation_Guide/index.html>

<!-- more -->

## 制作U盘启动工具

本例子环境为：Windows

可以使用 Fedora LiveUSB Creator(<https://fedorahosted.org/liveusb-creator/>) 或者 UltraISO 等工具来把系统写入 U盘，而后通过U盘启动来安装系统。

## 安装系统

从U盘启动，安装系统。安装中，会提示选择

* 默认选择 “Test this media & Install CentOS 7”

![](http://99btgc01.info/uploads/2015/05/001%288%29.jpg)


* 选择语言，设置时区

![](http://99btgc01.info/uploads/2015/05/002%284%29.jpg)

* 设置系统安装目录

![](http://99btgc01.info/uploads/2015/05/003%286%29.jpg)

* 设置 root 密码、创建新用户

![](http://99btgc01.info/uploads/2015/05/004%283%29.jpg)


## 配置静态IP

用 root 账户登录系统 修改 `/etc/sysconfig/network-scripts/ifcfg-ens33` 文件

    vi /etc/sysconfig/network-scripts/ifcfg-ens33
  
原先的配置是这样的

    TYPE=Ethernet
    BOOTPROTO=dhcp
    DEFROUTE=yes
    PEERDNS=yes
    PEERROUTES=yes
    IPV4_FAILURE_FATAL=no
    IPV6INIT=yes
    IPV6_AUTOCONF=yes
    IPV6_DEFROUTE=yes
    IPV6_PEERDNS=yes
    IPV6_PEERROUTES=yes
    IPV6_FAILURE_FATAL=no
    NAME=ens33
    UUID=e8fcc594-cd59-437a-8f98-d3fc74656f74
    DEVICE=ens33
    ONBOOT=no

ONBOOT 是默认不启动网卡的,改为 yes，然后再加上以下几个参数的设置,IPADDR0 指 IP 地址，GATWAY0 指网关，DNS1、DNS2 指 DNS。
  
    ONBOOT=yes
    IPADDR0=192.168.11.12
    GATWAY0=192.168.11.1
    DNS1=8.8.8.8
    DNS2=221.5.88.88 

![](http://99btgc01.info/uploads/2015/05/001%286%29.jpg)

## 测试

设置完成执行 service network restart 重启网络，而后 ping 下这个IP 做下测试