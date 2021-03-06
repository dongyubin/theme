---
title: 笔记本兼容性（中文版）
date: 2019-04-08 09:00:00
comments: true
tags:
    - 黑苹果
    - mac
categories:
	- 黑苹果
	- 指南
---

最好有Sandy Bridge，Ivy Bridge，Haswell或Broadwell，Skylake或Kaby Lake。



<!-- more -->



很多人在这里发帖询问“我的笔记本电脑能用吗”。我将尝试在本文中解决笔记本电脑的一些常见问题。

首先，我应该提到让笔记本电脑接近100％的功能总是很困难（除非笔记本电脑已经有很好的书面指南）并且可能无法实现或达到你想要的水平。这只是因为笔记本电脑的本质：你不能像桌面版本那样选择每个硬件组件（用于OS X兼容性）。

也就是说，大多数较新的笔记本电脑通常与macOS / OS X兼容，主要是因为基本组件由Intel CPU和Intel 6系列或7系列芯片组提供。如果您的笔记本电脑采用带有Intel CPU的英特尔显卡，那么您可以尝试使笔记本电脑与OS X配合使用。还支持一些专用的Nvidia / AMD设备，但往往会出现问题。

困难的地方在于所有其他硬件和变量...... 

有关其他信息，请参阅常见问题解答：[问题解答链接](https://www.tonymacx86.com/threads/faq-read-first-laptop-frequent-questions.164990/)

一般说明：

- CPU和芯片组系列：你需要知道你的笔记本电脑具有什么样的CPU。如果是Sandy Bridge，它的型号名称为iX-2xxx *。如果它是Ivy Bridge，它的型号名称为iX-3xxx *。Haswell（从10.8.5开始支持）是iX-4xxx *。Broadwell iX-5xxx，Skylake iX-6xxx和Kaby Lake iX-7xxx。您还应该注意您的芯片组版本，包括6系列，7系列，8系列，9系列，100系列。混合配置（例如7系列芯片组上的Sandy Bridge CPU）比未混合配置更难配置。

- 独立显卡：许多配备AMD Radeon或Nvidia GeForce独立显卡的笔记本电脑都采用切换机制，在情况需要时从集成显卡（Intel HD）切换到分立卡。这种类型的切换在OS X中不起作用，通常意味着禁用BIOS中的离散功能。如果您的BIOS不允许禁用它，则可能会使安装过程复杂化（您可能必须删除相关的kexts）。此外，即使你没有在OS X中使用它，分立卡仍然可以提供电源，所以试着找一台没有独立显卡的笔记本电脑。

- WiFi：OS X驱动程序支持的WiFi芯片数量有限。此外，OS X的WiFi驱动程序架构没有记录，因此OS X中没有很多WiFi驱动程序“Linux端口”。在这篇文章中有一些有用的OS X WiFi链接：[http：//www.tonymacx86.com /hp-probook/97099-wi-fi-bluetooth-cards-laptops-mac-os-os-x.html](https://www.tonymacx86.com/threads/wi-fi-and-bluetooth-cards-for-laptops-with-mac-os-os-x.97099/)。此外，一些BIOS实现已经实现了白名单，其中只有某些卡可以安装到笔记本电脑中，可能只有笔记本电脑制造商专门打造的卡。有时，白名单可以通过被黑客入侵的BIOS禁用，但有时BIOS是加密的。您的笔记本电脑的服务手册可能会为您提供兼容卡的列表，如果其中一个卡也恰好与OS X兼容，那么您可以搜索这样的卡并尝试更换它。一些更紧凑的笔记本电脑（超极本）将WiFi焊接到主板上或与其他组件（mSATA SSD）结合使用，使更换变得更加困难或昂贵。在许多情况下，购买时未指定笔记本电脑附带的特定WiFi芯片。

注意：兼容的WiFi芯片组及其工作程序如下所示：[http：//www.tonymacx86.com/network/104850-guide-airport-pcie-half-mini-v2.html](https://www.tonymacx86.com/threads/guide-airport-pcie-half-mini-v2.104850/)。未列出任何未列出的WiFi芯片，必须更换。另请阅读笔记本电脑FAQ（上面链接）。

- 以太网：以太网通常内置于笔记本电脑主板上。由于记录了OS X以太网驱动程序接口，因此可以使用相当多的开源驱动程序。通常你可以找到一个有效的，但并非总是如此。阅读笔记本电脑FAQ。

- 音频：使音频工作通常取决于寻找或创建修补的AppleHDA（为了获得最佳结果和稳定性，除非作为最后手段，否则不要使用VoodooHDA）。尽管可以为任何音频编解码器修补AppleHDA，但它非常复杂，需要您可能没有的技术技能，而且非常耗时。阅读笔记本电脑FAQ。

- 摄像头：大多数内置摄像头是USB，有些连接到USB2，有些连接到USB3。有些会起作用，有些则不起作用。没有模式，在你尝试之前没有办法告诉你。

- 读卡器：某些读卡器位于PCI总线上，并且可以从制造商处获得OS X驱动程序（例如，某些Jmicron设备）。有些是在USB总线上，可能使用内置于OS X的类驱动程序。在尝试之前你不会知道。

- 蓝牙：有时蓝牙内置于WiFi卡（在USB总线上），有时它在其他地方（在主板上？）。对于任何OS X黑客来说，蓝牙总是一个粗糙的地方，所以它可能无法满足您的需求。最好的结果是与兼容的Broadcom蓝牙硬件。使用Apple手表进行切换/热点/解锁等功能仍然不可靠。

- 电池状态：使用符合ACPI标准的AppleSmartBatteryManager.kext可以使电池状态正常工作。我一般推荐自己的kext：https：//github.com/RehabMan/OS-X-ACPI-Battery-Driver。大多数DSDT需要修补才能正常使用香草AppleACPIPlatform.kext（Ivy Bridge电源管理需要最新的AppleACPIPlatform.kext）。所需的修补程序通常特定于笔记本电脑系列，需要一些编程背景才能完成（除非您发现已经为您完成了修补程序）。请参阅笔记本电脑FAQ中的链接。

- 键盘/触控板：大多数笔记本电脑使用PS / 2接口作为键盘和触控板。OS X不支持PS / 2接口，因此您需要为其安装驱动程序。您在笔记本电脑中实际使用的触控板决定了您寻找的版本。大部分时间，触控板制造商都没有指定......即使使用相同型号的笔记本电脑，有时也会有所不同。甚至还有一个笔记本电脑被送去维修并带着来自不同供应商的触控板返回的情况。较新的计算机使用I2C作为触控板，这需要不同的驱动程序。这些驱动程序正在进行中。

- DSDT：大多数笔记本电脑都需要ACPI编辑才能使各种笔记本电脑功能正常工作。您应该准备好了解DSDT补丁，MaciASL，如何安装ACPI文件，以便引导加载程序（例如Clover）可以加载它们等。不要陷入为另一台笔记本电脑下载DSDT的陷阱。查找补丁并自行修补。笔记本电脑的原生DSDT可能会有所不同，即使是同一型号也是如此。我的ACPI修补指南与常见问题解答相关联。

- BIOS：某些BIOS实现对于启动很挑剔。例如，某些人不会将传统模式启动到GPT驱动器。OS X通常需要安装到GPT驱动器，因此这可能是一个问题。有一些解决方法，但有时这对非技术人员来说很难理解。

简而言之，黑客攻击笔记本电脑是一项挑战。你不应该期望它会很容易。并且有许多不同的笔记本电脑，每个都有独特的配置，BIOS，硬件组合等。即使上面提到的硬件似乎满足要求，给定的笔记本电脑总是可能无法工作。

如果你想要100％兼容独立显卡功能，完美的蓝牙，没有麻烦，不要吝啬...购买MacBook Pro。


关于gen1核心i系列CPU的注意事项

这些笔记本电脑通常使用OS X不能很好地支持的“Intel HD Graphics”。但有些报告称它可以运行。这里有一个相对广泛的文章：[http：//www.insanelymac.com/forum/topic/286092-guide-1st-generation-intel-hd-graphics-qeci/](https://www.insanelymac.com/forum/topic/286092-guide-1st-generation-intel-hd-graphics-qeci/)。因人而异。


关于Kaby Lake的注意事项

早期对Kaby Lake CPU和Intel HD620显卡的测试表明，它与Skylake的kexts具有良好的兼容性。Kaby Lake CPU要求使用具有相应CPUID的FakeCPUID（Clover选项）用于类似的Skylake CPU。并且图形可以与FakeID / IntelGFX和FakePCIID kexts一起使用。阅读笔记本电脑FAQ。


关于三星笔记本电脑和eDP显示器的注意事项

似乎很多三星笔记本电脑都与笔记本电脑液晶显示器有eDP连接，而不是更常见的LVDS。OS X中HD3000和HD4000的驱动程序不支持eDP。所以避免使用这样的三星笔记本电脑或至少验证它是否是eDP。

显然，HD5000（HD4400 / HD4600）OS X驱动程序中支持eDP，因此应该更好地支持Haswell（或更高版本？）系统上的eDP。目前的经验表明，eDP存在问题。