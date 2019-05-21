---
title: nuci5beh开机出现禁止符号，解决办法
date: 2019-05-06 09:00:00
comments: true
tags:
    - nuc8
    - nuc8i5beh
    - 黑苹果
    - mac
    - 禁止符
categories:
	- 黑苹果
	- 指南
top: 1
keywords:  [nuc8,nuc8i5beh,黑苹果,mac,禁止符]
---

![黑苹果](https://pic.rmb.bdstatic.com/2d0fae09224780bdb81d9341ea5a8bb2.jpeg)

<!-- more -->

#### 黑苹果开机有时会出现<code>Error allocating 0x11c8d pages at 0x0000000??????(每个人的都不同) alloc type 2</code> 错误，每次还得强制重启，让人很烦😫

#### 博主也尝试了很多的办法，但是就是没用，又是一个不小心发现了一个解决办法，赶紧尝试了一下，不试不知道，一试果然解决了。😆



### 错误截图：

![禁止符错误](../images/mac/jjfcw.jpg)



### 解决步骤：

```c
把bios更新到最新的版本的
把drivers64UEFI目录中AptioMemoryFix-64.efi替换为OsxAptioFix2Drv-free2000.efi
clover里边设置slide=0
```

### 相关文件下载地址

[OsxAptioFix2Drv-free2000.efi](http://www.mediafire.com/file/aks1kkyj6l1xf9n/OsxAptioFix2Drv-free2000.efi.zip)

