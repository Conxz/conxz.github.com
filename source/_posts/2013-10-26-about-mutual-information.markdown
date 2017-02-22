---
layout: post
title: "互信息杂谈"
date: 2013-10-26 22:14
comments: true
categories: Methods
tags: mutual information
---
谈到互信息，必然涉及到“信息”和“熵”两个概念。信息论的创始人Shannon给信息的定义是“用来消除不确定性的东西”；而在信息论中，熵表示的是不确定性的度量，不确定性越大，熵越高。对于一个熵越大的随机变量，需要越多的信息量来确定它的值。

而互信息是一个用来在信息论中衡量两个信号关联程度的度量，后其被用来对两个随机变量间的关联程度进行描述。互信息`I(X;Y)=H(X)-H(X|Y)`直观的意思就是知道了Y的值以后，我们对X的不确定性的减少量，即Y的值透露了多少关于X的信息量。`(Mutual information measures the reduction of uncertainty in X after observing Y. )`

互信息是非负的，也是对称的。当`I(X;Y)`远大于0时，表示二者关联度大；当`I(X;Y)=0`时，二者无关。且`I(X; Y) = I(Y; X)`。虽然，在某些计算互信息的工具包中二者并不相等。<!--more-->

值得注意的是，当X=Y时，互信息`I(X;X)=H(X)-H(X|X)=H(X)`，也就是说两个完全相互依赖的变量之间的互信息并不是一个常数，而是取决于它们的熵。

那互信息和常用相关是如何区别呢？在一篇MICCAI 2013的论文中提到：

The MI between two random variables measures the amount of information they share. The higher the MI value, the more ‘dependent’ the variables are, i.e. the more knowledge we gain of one by knowing the value of the other. MI should not be confused with the correlation between two variables, which measures the strength of the linear relationship between them. MI is much more general, as it does not assume any particular form for the relationship between the two variables.

这里提到关于`MI`和`Correlation`的区别，`Correlation`是线性的，也就是一阶的关联；而MI则没有假设关系的阶数，可以对应的理解为“无穷阶的关联”。

另外，`MI`的`X`和`Y`可以是一维的向量，也可以分别是多维的向量，具体取决于用于求解的工具。比如`MILCA`中提供了一个robust的`MI`的估计方法，`X`和`Y`都可以是多维的，而且它不需要用户提供X和Y的先验联合概率密度。

上面谈到`MI`和`Pearson’s correlation`的区别主要是非线性和线性的区别，平时我们还会用以下两个衡量非线性的测量：`Spearman’s rho` 和 `Kendall’s tau`。

But these two both measure monotonic relationship, thus neither of them can capture all types of non-linear dependency. Mutual information is one of the existing measures that can capture any type of non-linear relationship. So, mutual information is more general. 
