---
layout: post 
title: Win8-64bit-debug.exe
category: 科技
tags: [Assembly,资料]
matheq: no
comments: yes
toc: yes
share: yes
recentvisitors: yes
---

###问题

你正在学《汇编语言》，即将做第一个实验，

Win+R后输入cmd打开命令行，键入debug，然后...

```
'debug'不是内部或外部文件，也不是可运行的程序
或批处理文件
```

嗯，如果你是在64位系统下这么干的话。 

###为什么

debug是dos系统提供的实模式（8086方式）程序调试工具。[Wiki-Debug(command)](http://en.wikipedia.org/wiki/Debug_(command))
它本身是一个16位的应用程序。

在32位windows系统中，你可以进入虚拟的8086模式dos，进而运行debug。**但在64位系统中却不行。**

为什么？更详细的解释：[请戳我「为何没有Debug64.exe？」](http://blog.csdn.net/icansaymyabc/article/details/6097330)

###解决

1. 如果你的系统是Win7，那么你可以使用Windows XP Mode，在Win 7上运行专为Win XP设计的程序。**但Windows XP Mode不支持Win 8。**

>去微软官方处搞定：[Windows XP Mode](http://windows.microsoft.com/zh-CN/windows7/install-and-use-windows-xp-mode-in-windows-7)

2. 用dosbox模拟dos

>具体看这里[dosbox-jiusifeng-blog](http://blog.csdn.net/jiusifeng/article/details/8478831)

>[一个DOS模拟器](http://www.dosbox.com/wiki/Main_Page)

>[「百度文库」dosbox详细使用](http://wenku.baidu.com/view/cdda041552d380eb62946db2.html)

>mount：文件挂载命令。将某个文件夹路径挂载到某个地方去，只要访问了那个地方，那么也在访问那个文件夹。

3. 虚拟机

虚拟机上装32位的系统即可。更麻烦一点，双系统也可以。

###参考

[微软社区](http://answers.microsoft.com/zh-hans/windows/forum/windows_8-winapps/windows/e1c910ad-252f-4a54-8bec-19285f41e190)

[Stackoverflow](http://stackoverflow.com/questions/19661366/how-can-i-run-the-debug-command-from-windows-64x)

PS：windows下的程序调试工具：除去最熟悉的visual studio，还有轻量级的[windbg](http://www.pediy.com/kssd/pediy10/94457.html)

PPS：在找学习《汇编语言》的电子资源？[等会戳我](404)