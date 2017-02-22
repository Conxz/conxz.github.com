---
layout: post
title: "Install and Use R Package"
date: 2014-01-11 21:03
comments: true
categories: Tools
tags: R
---
**安装：**


- Method 1: 

Install from source
下载工具包, 比如irr包，用于计算ICC:
>$ R CMD INSTALL irr_0.84.tar.gz -l /my/own/R-packages/

注：这是在Linux的Terminal中完成的。


- Method 2: 

Install from CRAN directly:
> install.packages("irr", lib="/my/own/R-packages/")

注：这是在R中完成的。

上述两种方式有一个很明显的区别，即方法一不会自动下载安装irr包需要的依赖包，比如lpSolve包，而后一种方法则可以自动检查并下载需要的依赖包。


**使用：**

下面是如何使用R，在使用irr包中的函数之前，需要首先导入该包，也就是告诉R你需要调用哪个包里的函数，这个包在哪里：<!--more-->
> library("irr", lib.loc="/my/own/R-packages/")

其中lib.loc可以不用每次都输入，但是之前需要做如下操作：修改.bashrc文件中R lib路径的环境变量。

	export R_LIBS=${R_LIBS}:/my/own/R-packages/


在做Neuroimaging的数据处理时，我们更多的使用Python进行数据的读写和数学计算，虽然Python的数据计算工具包已经很强大，但是相较于R，Python还是略逊一筹。因此，有时候我们会借助R的工具包来辅助数据处理。在Python使用R的工具包，可以给Neuroimaging的数据处理带来不少的便利。为了达到这个目的，其中最常用的就是RPy了，新版本叫RPy2。下面演示如何在Python中调用R的工具包，比如我们刚才安装的irr。

	Import rpy2.robjects as robj
	r = robj.r
	r.library(‘irr’)


我们利用irr中的Intra-class correlation coefficient（ICC）来计算test-retest reliability：
	
	iccres = r.icc(ratings, model="twoway", type="agreement")

