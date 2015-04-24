---
layout: post 
title: 64位系统无法使用Debug
category: 科技
tags: [Assembly,资料]
matheq: no
comments: yes
toc: yes
share: yes
recentvisitors: yes
---

###问题

你正在学《汇编语言》，即将做第一个实验。

Win+R后输入cmd打开命令行，键入debug，然后...

`'debug'不是内部或外部文件，也不是可运行的程序`
`或批处理文件`

嗯，如果你是在64位系统下这么干的话。 

###为什么

debug是dos系统提供的实模式（8086方式）程序调试工具。

它本身是一个16位的应用程序。[Wiki-Debug(command)](http://en.wikipedia.org/wiki/Debug_(command))

在32位windows系统中，你可以进入虚拟的8086模式dos，进而运行debug。

**但在64位系统中却不行。**

为什么？更详细的解释：[请戳我「为何没有Debug64.exe？」](http://blog.csdn.net/icansaymyabc/article/details/6097330)

###解决

- 如果你的系统是Win7，那么你可以使用Windows XP Mode。

**但Windows XP Mode不支持Win 8。**

>去微软官方处搞定：[Windows XP Mode](http://windows.microsoft.com/zh-CN/windows7/install-and-use-windows-xp-mode-in-windows-7)

- 『推荐』用dosbox模拟dos环境运行debug.exe

先下载一个[debug.exe](http://pan.baidu.com/s/1c0s8A6c)（百度网盘：phdr）

再下载[dosbox](http://www.dosbox.com/download.php?main=1)（官网下载）[dosbox-meow](http://pan.baidu.com/s/1sj2r07r)（百度网盘：hmku）

运行dosbox（2个窗口共同作用，不要关闭其一），挂载debug.exe路径到某盘符。

>比如说我现在的debug.exe在D盘的Profess-Code文件夹中，而我想在C盘路径下运行debug.exe。

那么键入命令`mount c d:/Profess-Code`

>mount：文件挂载命令。将某个文件夹路径挂载到某个地方去，只要访问了那个地方，那么同时也在访问那个文件夹。

<a class="fancybox" rel="gallery1" href="http://ww2.sinaimg.cn/large/8935112btw1eqlv80zshpj20hy0bx0vo.jpg" title="英文输入:区分大小写"><img src="http://ww2.sinaimg.cn/large/8935112btw1eqlv80zshpj20hy0bx0vo.jpg" alt="英文输入:区分大小写" /></a>

之后来到该盘符下c:，键入debug，搞定！

<a class="fancybox" rel="gallery1" href="http://ww4.sinaimg.cn/large/8935112btw1eqlv8n65r6j20hy0bx0vp.jpg" title="Have fun!debug"><img src="http://ww4.sinaimg.cn/large/8935112btw1eqlv8n65r6j20hy0bx0vp.jpg" alt="Have fun!debug" /></a>

Tips: 整合以上命令，使得一运行dosbox就可以debug。
到dosbox的安装目录下找到文件`DOSBox 0.74 Options.bat`，在文件尾部的[autoexec]加入启动运行代码。

```
[autoexec]
# Lines in this section will be run at startup.
# You can put your MOUNT lines here.
mount c d:/Profess-Code
c:
debug
```

- 虚拟机（比如：VMware Workstation）

在虚拟机上装32位的系统（比如windows xp）即可。更麻烦一点，双系统也行。

###参考

[「jiusifeng」-简单使用dosbox](http://blog.csdn.net/jiusifeng/article/details/8478831)

[「百度文库」-详细使用dosbox](http://wenku.baidu.com/view/cdda041552d380eb62946db2.html)

[dosbox官方介绍](http://www.dosbox.com/wiki/Main_Page)

[微软社区-windows64位系统怎么不能进入debug？](http://answers.microsoft.com/zh-hans/windows/forum/windows_8-winapps/windows/e1c910ad-252f-4a54-8bec-19285f41e190)

[Stackoverflow-how-can-i-run-the-debug-command-from-windows-64x](http://stackoverflow.com/questions/19661366/how-can-i-run-the-debug-command-from-windows-64x)

PS：windows下的程序调试工具：除去visual studio，还有轻量级的[windbg](http://www.pediy.com/kssd/pediy10/94457.html)

PPS：在找学习《汇编语言》的电子资源？[等会戳我](http://pan.baidu.com/s/1eQerIim)（百度网盘：ifky）