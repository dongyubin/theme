---
title:   软件测试的转化篇，从基础开始
date: 2019-04-30 09:00:00
comments: true
tags:
    - 软件测试
    - 服务端口
    - Tomcat
    - Mysql
    - hosts
    - 端口
categories:
	- 技术
	- 软件测试
---

![软件测试基础](https://s2.ax1x.com/2019/03/18/AmBQud.jpg)

<!-- more -->

## 常见的服务和默认端口、协议：

- http(超文本传输协议)：80
- FTP（文件传输协议）:20、21
- Smtp：25
- Pop3：110
- IMAP:143
- DNS:53
- Ssh:22
- Mysql:3306
- Oracle:1521
- Sql Server:1433
- Tomcat:8080
- Telnet:23
- Https:443 

## Tomcat目录介绍：

- bin:存放二进制的可执行程序的目录
- conf:存放tomcat的配置文件的目录
	- server.xml:tomcat服务端配置文件比如：端口、部署路径、虚拟目录等
- logs:日志文件路径
	- catalina.xxx.log（默认日志文件-win下）
	- catalina.out（默认日志文件-Linux下）
- temp:存放临时文件目录
- webapps:存放tomcat的项目部署默认位置

## Mysql中常用的命令：

```cmd
mysql>source xxx.sql;		#导入sql文件
mysql>show databases;		#查看存在的数据库
mysql>use redmoonoa;		#使用某个库
mysql>show tables;		#查看库中所有的表
```

## windows下hosts文件的位置：

	C:\Windows\System32\drivers\etc\hosts

## windows下的快捷键：

[完整快捷键](https://support.microsoft.com/zh-cn/help/12445/windows-keyboard-shortcuts)

- 快速打开系统应用程序（win+R） 
	- Notepad   记事本 
	- Write  写字板 
	- Mspaint  绘图程序 
	- Calc   计算器 
	- Osk   屏幕键盘 
	- Mstsc  远程桌面连接 
	- appwiz.cpl   安装卸载程序 
	- inetcpl.cpl   打开internet选项

## 计算机的计量单位

- .b     B  KB   MB  GB   TB   PB、EB 、ZB、YB 、NB、DB 
- bit    byte b-位   B-字节   B=8b      KB= 1024B  MB=1024KB

## 带宽的接入用的是b 位， 假如你家100M电信接入

- 意思是： 理论上100Mb/s =12.5MB/s 

## 上网的过程：

```cmd
访问www.baidu.com 
1. 浏览器地址栏敲入的www.baidu.com  ——>回车
2. 操作系统OS找对应的域名对应IP （域名解析）
3. 由本地的操作系统查找对应的DNS服务器（服务的端口号：23端口）
	1. 在此之前： 先从本地浏览器缓存找域名和ip对应关系，如果能找到就直接请求这个IP。
	2. 如果浏览器缓存找不到： 开始找操作系统配置文件c:\windows\system32
	3. 如果还找不到再从网络设备上查找（路由器等）
	4. 如果还找不到就请求DNS服务器，获取对应的域名和IP对应关系
4. 把请求向对应的IP地址的服务器发送。
5. 服务器接收请求，进行处理。
6. 服务器处理完成后，把对应的图片、js、css、字体、声音等传输给客户端。
7. 浏览器接收这些素材，进行渲染。
```

## 查看计算机中QQ进程开启的端口信息

```cmd
cmd下：
>tasklist|findstr QQ
>netstat -ano|findstr 端口号
>taskkill /im xxx进程      #结束进程
```