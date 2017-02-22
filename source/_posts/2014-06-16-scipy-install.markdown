---
layout: post
title: "Scipy安装步骤"
date: 2014-06-16 19:15
comments: true
categories: Tools
tags: python
---
Scipy函数库是基于python做科学和工程计算中常用的库，其中包括了众多的线性代数、数值计算、图像和信号处理、稀疏矩阵等。在基于python做脑影像处理时，scipy也是最常用到的python库之一。下面记录安装scipy的步骤，备查。

系统环境：Centos 5.7 64bit

在非root权限下，需要把库安装在自己有权限的目录下，比如采用pip提供的—user参数将默认安装到.local/lib/python2.7/site-packages/中。

安装scipy涉及到的主要命令如下：

	pip install –user scipy

不过一般情况下，你会碰到如下的问题：<!--more-->

	Blas (http://www.netlib.org/blas/) libraries not found.

Scipy网站上有说到，scipy会依赖该库，需要首先安装，安装步骤如下：

	mkdir -p ~/src/
	cd ~/src/
	wget http://www.netlib.org/blas/blas.tgz
	tar xzf blas.tgz
	cd BLAS
	gfortran -O3 -std=legacy -m64 -fno-second-underscore -fPIC -c *.f
	ar r libfblas.a *.o
	ranlib libfblas.a
	rm -rf *.o
	export BLAS=~/src/BLAS/libfblas.a

注：我使用的服务器安装的fortran编译器是gfortran，这一步根据具体情况决定。

实际上，scipy安装还依赖另一个库LAPACK，需要采用类似的方式安装：

	cd ~/src/
	wget http://www.netlib.org/lapack/lapack.tgz
	tar xzf lapack.tgz
	cd lapack-*/
	cp INSTALL/make.inc.gfortran make.inc
	make lapacklib
	make clean
	export LAPACK=~/src/lapack-*/libflapack.a

注：在make lapacklib之前可能需要编辑make.inc文件，将OPTS 和 NOOPT如下：`OPTS = -O2 –fPIC`和`NOOPT = -O0 –fPIC`

如此，在安装完BLAS和LAPACK后，就可以顺利安装scipy了。
