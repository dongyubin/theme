---
title: 指南：nuc8i5beh安装黑苹果的教程，接近完美运行
date: 2019-04-01 09:00:00
comments: true
tags:
    - nuc8
    - nuc8i5beh
    - 黑苹果
    - mac
    - 指南
categories:
	- 黑苹果
	- 指南
top: 3
keywords:  [nuc8,nuc8i5beh,黑苹果,mac,指南]
---

![黑苹果](https://pic.rmb.bdstatic.com/2d0fae09224780bdb81d9341ea5a8bb2.jpeg)


<!-- more -->


### 采购硬件设施
- nuc8i5beh

- 镁光m.2 1100 256固态硬盘

- 三星 DDR4 2400笔记本内存条

- HKC电脑显示器

- 8G U盘（这个之前有，不属于采购的）


### 所需软件
- Mojave 10.14.2
  [百度网盘](https://pan.baidu.com/s/1NJnLGri673BnBqDvOibduA)

- balenaEtcher：
  [官网](https://www.balena.io/etcher/)

- bios65文件：
  [下载地址](https://www.tonymacx86.com/attachments/be0056-bio-zip.392463/)

- nuc8 安装软件包：
  [百度云](https://pan.baidu.com/s/1fHmO1p-9tffcw0-rRYj4VA) 提取码：t0gk

- EFI文件

  [github地址](https://github.com/dongyubin/nuc8i5beh)
### 安装过程
1. 在Windows下插入U盘，启动balenaEtcher，“<code>select image</code>”选择“<code>Mojave 10.14.2</code>”镜像,选择U盘，点击“<code>Flash</code>”即可

![etcher](https://7.daliansky.net/etcher.png)

### 注意：
- BIOS更新到版本<code>0056</code>
- 在SSD上选择<code>APFS</code>分区
- 最好先安装<code>10.14.2</code>，再升级
- mac版本可以升级到最新版本<code>10.14.4</code>（博主已更新到<code>mac mojave beta 10.14.5</code>）

### 显示EFI分区

Windows系统下，用【管理员身份】打开【CMD】窗口，输入以下命令：

```cmd
c:\>diskpart
list disk           # 磁盘列表
select disk n       # 选择EFI分区所在的磁盘，n为磁盘号
list partition      # 磁盘分区列表
select partition n  # 选择EFI分区，n为EFI分区号
set id="ebd0a0a2-b9e5-4433-87c0-68b6b72699c7"	# 设置为基本数据分区
assign letter=X     # x为EFI分区盘符
exit				# 退出diskpart
```

### BIOS设置

1. 将下载好的BIOS56文件里的【<code>BE0056.bio</code>】拷贝到一个空白U盘根目录
2. 启动nuc，按【<code>F7</code>】，选择BE0056.bio，去更新BIOS
3. 更新后，再次启动nuc，按【<code>F2</code>】，进入BIOS设置界面
4. BIOS设置如下：
	- « Inter VT for directed I/VO (VT-d) » ： <code>disabled</code>
	- « Secure Boot » ： <code>disabled</code>
	- « Legacy Boot » ：<code>enabled</code>
	- « Fast Boot » ： <code>disabled</code>
	- Boot->Boot Devices-> « USB » ： <code>enabled</code>
	- SATA mode ： AHCI
	- Boot->Boot Configuration-> « Boot Network Devices Last » ： <code>disabled</code>
	- Power->Secondary Power Settings, « Wake on LAN from S4/S5 », set to « <code>Stay Off</code> »
	- Devices->Video, « IGD Minimum Memory » set to <code>64mb</code>
	- Devices->Video, « IGD Aperture Size » set to <code>256mb</code>

#### 注意：

##### 不打勾为disable，打勾为enabled

### 使用Clover UEFI在NUC上引导macOS安装程序
1. 将U盘插入需要安装系统的电脑
2. 显示Clover引导界面，需要设置FakeID（<code>Clover Options -> Graphics Injector -> FakeID</code>）
	- 点击 « Enter » 键去修改，改为： <code>0x12345678</code>
	- 按« Return »两次，返回到Clover引导界面
3. 选择« Boot macOS Install from install_osx »，按« Enter » 键即可
4. 出现安装界面，选择【<code>磁盘工具</code>】将你的SSD，格式化为【<code>APFS</code>】格式
5. 选择“<code>安装mac OS</code>”，安装系统即可【<code>重启后，请再次执行步骤2</code>】
6. 安装成功后，进入系统
7. 打开 <code>Clover Configurator</code>,左侧列表里选择<code>Mount EFI</code>，如下图：

![Clover Configurator](http://tangwumo.com/wp-content/uploads/2018/10/%E6%89%93%E5%BC%80clover-configurator%E6%8C%82%E8%BD%BDEFI%E5%88%86%E5%8C%BA.jpg)

8. 点击【<code>Efi Partitions</code>】下的【<code>Mount Partition</code>】，输入密码，点击【<code>Open Partition</code>】，打开EFI文件夹
9. 将U盘里的【<code>BOOT</code>】文件夹和【<code>CLOVER</code>】文件夹拷贝到【<code>步骤8</code>】的EFI文件夹下即可（这样启动系统就再也不用插U盘了）
10. 在此链接下，下载【<code>config_nuc8_bc.plist</code>】:[https://github.com/RehabMan/Intel-NUC-DSDT-Patch](https://github.com/RehabMan/Intel-NUC-DSDT-Patch)
11. 下载完，重命名为：【<code>config.plist</code>】，拷贝到【<code>步骤8</code>】的EFI文件夹下的【<code>CLOVER</code>】文件夹下，替换即可。
12. 如有不懂的，可以参考外国大神的教程：[大神教程](https://www.tonymacx86.com/threads/guide-installing-macos-mojave-10-14-2-on-intel-nuci5beh-using-clover-uefi.268502/)

### 不足之处

1. 无线网（无解）
2. 雷电3不支持热插拔
### 体验效果
1. 运行流畅​
2. icloud也可以使用（心里美滋滋😃 ）
### 成功展示图

![iMac](https://pic.rmb.bdstatic.com/bd012b6d537ad323abfe5dc9cb7e3e21.png)

![显示器](https://pic.rmb.bdstatic.com/2000e391ba631d17bd03ea91e8f93518.png)

### 如有不懂之处，可在下方留言

### 或者直接联系博主ＱＱ:892457803