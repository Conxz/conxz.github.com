---
layout: post
title: "Paired t or two-sample t-test"
date: 2014-04-12 13:27
comments: true
categories: Methods
tags: [paired t-test, two-sample t-test]
---
之所以谈这两种t检验方法，是因为一篇很有意思的问题，即Neurobiological basis of head motion in brain imaging。在介绍完两种t检验方法后在回来谈论这篇文章。

双样本t检验Two-sample t-test  |  配对t检验Paired t-test

双样本t检验，也叫独立样本t检验。即考查两个相互独立的样本的均值的差异。（与配对t检验相比，这里的两组样本是没有配对信息的，比如比较男生和女生在方向感能力上的差异）

![f1](/images/post_images/f1.jpg "f1")

其中s1和s2分别为两个样本的标准差，n1和n2为两个样本的样本量。此时，t值的自由度为n1-1和n2-1中较小的一个。

	Note: 在假设两个样本的variance相等的情况下，自由度为n1+n2-2，这也是我们常见的自由度计算方式，SPSS中给出了假设方差相等的自由度，以及方差不等时根据两个样本各自的方差和样本量估计的自由度。感谢@斯图拉特 童鞋提醒 :)

当n1=n2=N时，可以简化为

![f2](/images/post_images/f2.jpg "f2")

这时候自由度为n1+n2-2，即2N-2。<!--more-->

在配对t检验中，两组样本是有配对关系的（n1=n2=N），比如考查睡眠剥夺前后被试在警觉性上的变化。计算时，首先计算配对样本的差值，差值的均值记为(x_∆ ) ̅，差值的标准差记为s_∆。

![f3](/images/post_images/f3.jpg "f3")

自由度为N-1。
对上式进行展开，结果如下：

![f4](/images/post_images/f4.jpg "f4")

考虑到一般情况下，配对的两个样本是相互依赖的，他们之间在更多的时候是不独立的，加入他们之间的相关值为r，则当r大于0值，

![f5](/images/post_images/f5.jpg "f5")

即计算得到的t值比在独立样本的情况下得到的t值要大。在样本量不是很少的情况下，配对的设计更容易显著。
当r小于0时，则相反，在配对的设计中这种情况极少。
而在r=0时，得到的t值与双样本的情况相同，不过由于配对设计中自由度相对较小，在显著性上会少小一些，不过当样本量足够大时，这种在显著性上的差异是基本可以忽略的。

**综上，假设两组样本的数据不变，如果两组样本存在一定的正向依赖关系，在配对的设计中得到的t值会更大一些，也就是容易得到结果。**

思考：

*Zeng et al., 2014, Neurobiological basis of head motion in brain imaging, PNAS*

这篇文章为了区分head motion影响MRI信号，和MRI参数反映了在head motion上的个体差异，提出了一个很惊艳的设计：即分别采用被试内和被试间的比较，如果在被试间的比较中，高head motion组在MRI参数上和低head motion组存在显著差异，而被试内的比较中没有发现这种差异，则可以在一定程度上说明，head motion与MRI参数的相关，不能用简单的motion影响MRI信号来解释，还存在另一种可能，即MRI参数反应了head motion的neurobiological basis。

那么这篇文章和上面讲述的两种检验有什么关系呢？事实上，这篇文章中就是两个实例，在被试间分析中采用two-sample t-test，而在被试内分析中采用了paired t-test。

这些咋看上去没有问题，不过细看文章内容，发现作者的这些数据是从一个3000+的数据库中select出来的，有句话说的话，如果去select的话，什么样的结果select不出来呢。还好作者做了各种验证，在一定程度上堵上了一些爱挑剔的人的嘴。

不过话又说回来，根据文章的描述，作者在被试间分析中用到的样本共56对，是的，你没看错，是56 pairs。这里作者对每一对都根据扫描的scanner，coil，sex，age等各种信息做了匹配（也就是配对啦）。这时候就会想了，既然已经配对好了，为什么不采用配对t-test呢。考虑到MRI数据一方面受到严重的scanner，coil的影响，另一方面也有显著的sex difference，和age effects，因此，这里两个样本可能并不是相互独立的，也就可能并不满足独立样本t样本的基本假设。

从上面关于独立样本t检验和配对t检验的基本原理的分析可以发现，其实在这里采用独立样本t检验其实是更保守的一种做法，也就是说即使采用配对t检验也不至于导致现在报告的结果消失掉。但是，**有没有可能在采用合适的检验方法后倒是“全脑亮起”呢？**

参考文献：

- Standard Error, [http://en.wikipedia.org/wiki/Standard_error](http://en.wikipedia.org/wiki/Standard_error)


- Neurobiological basis of head motion in brain imaging, [http://www.pnas.org/content/early/2014/04/02/1317424111.abstract](http://www.pnas.org/content/early/2014/04/02/1317424111.abstract)


- Student's t-test, [http://en.wikipedia.org/wiki/Student's_t-test](http://en.wikipedia.org/wiki/Student's_t-test)


- Should I Use a Paired t or a 2-sample t? [http://blog.minitab.com/blog/statistics-and-quality-data-analysis/t-for-2-should-i-use-a-paired-t-or-a-2-sample-t](http://blog.minitab.com/blog/statistics-and-quality-data-analysis/t-for-2-should-i-use-a-paired-t-or-a-2-sample-t)


- Two Sample t test for Comparing Two Means, [http://www.cliffsnotes.com/math/statistics/univariate-inferential-tests/two-sample-t-test-for-comparing-two-means](http://www.cliffsnotes.com/math/statistics/univariate-inferential-tests/two-sample-t-test-for-comparing-two-means)
