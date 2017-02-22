---
layout: post
title: "AFNI安装/AFNI Installation"
date: 2014-08-20 17:09
comments: true
categories: Tools
tags: afni
---
除了FSL和SPM，AFNI也是研究者常用的脑影像处理工具。官方提供了详尽的安装步骤（非管理员权限），点[我](http://afni.nimh.nih.gov/pub/dist/HOWTO/howto/ht00_inst/html/linux_inst_basic.html)。这里做一些补充。

根据[官方安装步骤](http://afni.nimh.nih.gov/pub/dist/HOWTO/howto/ht00_inst/html/linux_inst_basic.html)的说明，在安装AFNI之前，需要首先安装几个依赖的package，包括libXp, tcsh，PyQt4, 和R。安装步骤参看上面提及的链接，下面几条命令用于检查自己的机器是否安装完成了上述依赖package。

	rpm -qa | grep libXp
	rpm -qa | grep tcsh
这两条命令会在terminal中print出相应package的文件名。
	
	which R
正常情况下，上面这条命令会print出R的路径。

PyQt4是Python的一个工具包，下面检查是否安装完成PyQt4.

	ipython
	>from PyQt4 import QtCore
	>
在Python中输入第二条命令后如果没有报错，就是安装完成了。

接下来可以按照[官方安装步骤](http://afni.nimh.nih.gov/pub/dist/HOWTO/howto/ht00_inst/html/linux_inst_basic.html)完后进行。在选择AFNI的版本时，如果机器有多个CPU，可以选`linux_openmp`或64位系统的`linux_openmp_64`;只有一个CPU的话，可以选`linux_xorg7`或`linux_xorg7_64`。

我用的Centos7，环境变量PATH采用`~/.bashrc`控制，而不是官方安装步骤中的.cshrc，所以在`~/.bashrc`中添加如下几行即可：<!--more-->

	\# AFNI Configuration
	AFNIDIR=~/opt/bin/abin
	PATH=${AFNIDIR}:${PATH}
	export AFNIDIR PATH
其中`~/opt/bin/abin`是我的AFNI的安装目录。

设置好环境变量后，关闭这个terminal，重新打开一个新的terminal，安装成功的话，输入`afni`会打开afni的界面。

另外，输入如下两个命令可以分别检查AFNI需要的Python工具包和R，以及它们各自的依赖package是否正常。

	python_module_test.py
	3dMEMA

