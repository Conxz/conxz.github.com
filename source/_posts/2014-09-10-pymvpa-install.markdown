---
layout: post
title: "PyMVPA安装"
date: 2014-09-10 21:49
comments: true
categories: Tools
tags: [python, mvpa]
---
多体素模式分析(multi-voxel pattern analysis, MVPA)是一种基于机器学习理论发展出来的一种功能磁共振数据分析技术，简单说，就是通过多个体素的信息融合在一起用于后续的预测等统计分析。具体实现上，PyMVPA是研究者常用的一个工具包。下面记录PyMVPA安装步骤，备查。

系统环境：Centos 5.7 64bit 非root用户

和[Scipy安装方法](http://www.conxz.net/blog/2014/06/16/scipy-install/)类似，主要涉及如下命令：

	# pip install --user pymvpa2
如果安装顺利，会显示如下文字，表示安装完成：
	
	Successfully installed pymvpa2
	Cleaning up...

但是，更多的可能会碰到如下问题：

	unable to execute 'swig': No such file or directory
	error: command 'swig' failed with exit status 1
这个报错说明需要首先另外安装这个叫swip的工具，实际上，SWIG可以允许一些脚本语言调用C/C++语言的接口。支持的语言有：Perl, Python, Tcl, Ruby, Guile, and Java。在PyMVPA中主要就是涉及与Python的对接了。安装SWIP步骤如下：<!--more-->
首先下载最新版本的安装包 [http://www.swig.org/download.html](http://www.swig.org/download.html)，放到某个目录下。然后依次执行如下命令：

	# tar -xzvf swig-3.0.2.tar.gz
	# ./configure --without-pcre --prefix=/nfs/j3/userhome/sean/opt/
	# make
	# make install
其中，第一行将压缩包解压；
第二行中，前面的参数`--without-pcre`表示忽略Perl-compatible regular expression library，后面的参数`--prefix`用于指定后续安装的目录，因为这里是非root用户安装，需要指定一个自己有读写权限的目录；
第三、四行用于完成编译安装，显示Installation complete。
此时，重复PyMVPA的安装命令即可。
