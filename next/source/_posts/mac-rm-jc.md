---
title: 黑苹果安装入门教程，新手必看
date: 2019-05-08 09:00:00
comments: true
tags:
    - 黑苹果
    - mac
    - 入门教程
    - 入门
categories:
	- 黑苹果
	- 指南
top: 2
keywords:  [黑苹果,mac,入门教程，入门]
---

![黑苹果](https://pic.rmb.bdstatic.com/2d0fae09224780bdb81d9341ea5a8bb2.jpeg)


<!-- more -->

### “黑苹果”是什么？

##### 自从苹果采用Intel的处理器，OS X被黑客破解后可以安装在Intel CPU与部分AMD CPU的机器上。从而出现了一大批非苹果设备而使用苹果操作系统的机器，被称为黑苹果(Hackintosh)；在Mac苹果机上面安装原版Mac系统的被称为白苹果（Macintosh），与黑苹果相对。（百度百科）

### 引导+镜像搭配方案：

##### UEFI+GPT+Clover引导教程（你机器支持UEFI，那么小编强烈建议你用clover+原版）

##### BIOS+MBR+Chamelon或BIOS+GPT+Chamelon引导教程（懒人版）

### U盘引导启动

##### **Clover（四叶草）**是目前主流的黑苹果引导软件，他的作用就是骗过苹果操作系统，让苹果系统以为你是在一台"合法“的白苹果设备上使用它。

##### <code>先做clover引导u盘安装程序，有的下载映像是自带CLOVER的，写入U盘就行</code>

##### 开始编辑config.plist，这个文件就是Clover的针对不同系统的配置文件，那么你就需要根据自己的硬件配置，可以使用Clover Configurator打开该文件。config.plist这个文件是整个黑苹果世界里最邪恶的存在，没有之一。同时，它的重要性也如同它的邪恶程度一样，独一无二。你的冒牌苹果电脑每次启动的时候要虚拟什么、重建什么、加载什么、绕开什么，统统都要听命于它。如果整个clover程序是一台电脑，那config.plist就相当于是这台电脑的CPU。

##### 这个文件的位置在你<code>启动U盘EFI的EFI>CLOVER目录</code>下。

##### <code>FakeSMC.kext</code>是仿冒苹果SMC设备的驱动文件，说白了就是欺骗苹果系统我是苹果的设备，通常OS X是无法安装在普通PC的，所以我们要用FakeSMC欺骗过去。建议所有黑苹果用户更新到最新版本，可以解决不少问题。

##### 只要你的机器不是真正的苹果机，那么，在PC上安装的苹果系统，无论是所谓的原版或者是破解版，都至少要安装一个名为fakesmc.kext（以前用AppleDecrypt.kext或dsmos.kext）的核心破解驱动，否则到目前为止，非苹果机器是不能运行的（进不了系统界面）

##### 以上就是做启动盘所必须的东西，结束后有两个U盘（EFI引导盘和启动安装盘）：把刚才你下载的或者制作的config.plist这个文件，拖到启动U盘EFI的EFI>CLOVER目录下，覆盖原来。

##### 来到启动U盘的<code>EFI>CLOVER>kexts</code>，把下面FakeSMC.kext解压后放到other这个文件夹里去。kexts文件夹里的其他目录可以删掉。

### 一些常用“术语”：
<code>kext</code>：全称 Kernel Extensions 也就是我们常说的“驱动”
<code>L/E</code>：/Library/Extensions
<code>S/L/E</code>：/System/Library/Extensions
<code>E/E</code>：/Extra/Extensions （这个是变色龙独有的，用于放入其他第三方驱动，Clover不识别此文件夹，即没有“Extra”的概念）
<code>Kexts/other</code>：/EFI/Clover/Kexts/other（这个是Clover的第三方驱动目录）

[庆贺N卡继续支持10.13，发正式版镜像和一些安装需要注意的地方](http://bbs.pcbeta.com/viewthread-1759895-1-1.html)