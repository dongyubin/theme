---
title: Guide:nuc8i5beh install black apple tutorial, close to perfect operation
date: 2019-05-16 09:00:00
comments: true
tags:
    - nuc8
    - nuc8i5beh
    - Black apple
    - mac
    - Guide
categories:
	- 黑苹果
	- 指南
top: 3
keywords:  [nuc8,nuc8i5beh,Black apple,mac,Guide]
---

![黑苹果](https://pic.rmb.bdstatic.com/2d0fae09224780bdb81d9341ea5a8bb2.jpeg)


<!-- more -->


### Purchase hardware facilities
- nuc8i5beh

- Magnesium m.2 1100 256g solid state hard drive

- Samsung DDR4 2400 notebook memory

- HKC computer monitor

- 8G U disk (this was previously, not part of the purchase)


### 所需软件
- Mojave 10.14.2
  [Baidu network disk](https://pan.baidu.com/s/1NJnLGri673BnBqDvOibduA)

- balenaEtcher：
  [Official website](https://www.balena.io/etcher/)

- bios65 file：
  [download link](https://www.tonymacx86.com/attachments/be0056-bio-zip.392463/)

- nuc8 Installation package：
  [network disk](https://www.lanzous.com/b737011/) Extraction code：i21t

- EFI file

  [Github address](https://github.com/dongyubin/nuc8i5beh)
### 安装过程
1. Insert a USB flash drive under Windows，Start balenaEtcher，“<code>select image</code>”select“<code>Mojave 10.14.2</code>”Mirror,Select U disk，Click on "<code>Flash</code>"

![etcher](https://7.daliansky.net/etcher.png)

### note：
- BIOS update to version <code>0056</code>
- Select <code>APFS</code> partition on the SSD
- It is best to install <code>10.14.2</code> first, then upgrade
- The mac version can be upgraded to the latest version <code>10.14.4</code> (the blogger has been updated to <code>mac mojave beta 10.14.5</code>)

### Display EFI partition

Under Windows system, open the [CMD] window with [Administrator Identity] and enter the following command:

```cmd
c:\>diskpart
list disk           # Disk list
select disk n       # Select the disk where the EFI partition is located, where n is the disk number.
list partition      # Disk partition list
select partition n  # Select EFI partition, n is the EFI partition number
set id="ebd0a0a2-b9e5-4433-87c0-68b6b72699c7"	# Set as basic data partition
assign letter=X     # x is the EFI partition drive letter
exit				# Exit diskpart
```

### BIOS settings

1. Copy [<code>BE0056.bio</code>] in the downloaded BIOS56 file to a blank U disk root directory.
2. Start nuc, press [<code>F7</code>], select BE0056.bio, and update the BIOS.
3. After the update, start nuc again, press [<code>F2</code>] to enter the BIOS setup interface.
4. The BIOS settings are as follows:
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

#### note：

##### Do not tick for disable, tick to enable

### Boot the macOS installer on NUC using Clover UEFI
1. Insert the USB flash drive into the computer where the system needs to be installed.
2. To display the Clover boot interface, you need to set the FakeID (<code>Clover Options -> Graphics Injector -> FakeID</code>)
	- Click the « Enter » button to modify it and change it to： <code>0x12345678</code>
	- Press « Return » twice to return to the Clover boot interface
3. Select « Boot macOS Install from install_osx » and press « Enter »
4. The installation interface appears. Select [<code>Disk Tools</code>] to format your SSD as [<code>APFS</code>] format.
5. Select "<code>install mac OS</code>", install the system. [<code> restart, please perform step 2</code> again]
6. After the installation is successful, enter the system
7. Open <code>Clover Configurator</code> and select <code>Mount EFI</code> in the list on the left, as shown below:

![Clover Configurator](http://tangwumo.com/wp-content/uploads/2018/10/%E6%89%93%E5%BC%80clover-configurator%E6%8C%82%E8%BD%BDEFI%E5%88%86%E5%8C%BA.jpg)

8. Click [<code>Mount Partition</code>] under [<code>Efi Partitions</code>], enter the password, and click [<code>Open Partition</code>] to open the EFI folder.
9. Copy the [<code>BOOT</code>] folder and the [<code>CLOVER</code>] folder in the USB flash drive to the EFI folder of [<code>Step 8</code>]. (This way you no longer need to plug in the U disk when you start the system)
10. Under this link, download [<code>config_nuc8_bc.plist</code>]:[https://github.com/RehabMan/Intel-NUC-DSDT-Patch](https://github.com/RehabMan/Intel-NUC-DSDT-Patch)
11. After downloading, rename it to: [<code>config.plist</code>] and copy it to the [<code>CLOVER</code>] file in the EFI folder of [<code>Step 8</code>]. Clip it and replace it.
12. If you don't understand, you can refer to the tutorial of foreign gods.：[Great God Tutorial](https://www.tonymacx86.com/threads/guide-installing-macos-mojave-10-14-2-on-intel-nuci5beh-using-clover-uefi.268502/)

### Inadequacies

1. Wireless network (no solution)
2. Thunder 3 does not support hot swap
### Experience effect
1. Smooth operation
2. Icloud can also be used (in my heart)
### Successful display

![iMac](https://pic.rmb.bdstatic.com/bd012b6d537ad323abfe5dc9cb7e3e21.png)

![显示器](https://pic.rmb.bdstatic.com/2000e391ba631d17bd03ea91e8f93518.png)

### If you don't understand, please leave a message below

### Or directly contact the blogger QQ: 892457803

### [Chinese version](https://chengxuxiaohei.cn/mac-anzhuang.html)

