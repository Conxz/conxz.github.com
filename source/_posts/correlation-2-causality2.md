---
title: 从相关到因果2
date: 2012-07-16 23:10:27
tags:
---
相关在日常的研究中常涉及到，‘相关correlation’是指一大类统计两个随机变量或两组数据之间关系的方法。常用的计算相关的方法有Pearson correlation， Spearman correlation以及partial correlation，Kendall’s Tau等多种。其中，相关系数r (Pearson correlation coefficient)尤为常用，r从-1到1，r越接近于-1或1，表示两个变量越相关related；当r靠近0时，表示两个变量之间没有关系。因此，相关系数表示两个变量共变的程度。另外，相关系数还有一种理解，即r的平方与一个变量与另一变量相关related的变异占该变量变异的百分比相等。

Correlation r to p

在相关报告中，同时会在r的后面跟上一个p值，表示统计结果的显著性，即报告的相关多大程度上是由随机抽样误差带来的，而这个随机误差是和样本量相关的，这样样本量就会直接影响相关值的显著性。说到底，这里涉及对相关系数的显著性检验，即样本相关系数与总体相关系数的差异检验。根据总体相关系数可以分为两种情况：ρ=0和ρ≠0。

![correlation](/images/post_images/p256.jpg "correlation")

如果H0设为ρ=0，那么通过下面的式子对r做t检验即可得到相应的显著值。

T=(r-0)/sqrt((1-r^2)/(n-2))

人们常说的“相关系数r是显著的”一般都是指的ρ=0的前提下的检验结果，即回答两个变量是否相关的问题。

在特殊需求是，为了回答r是否来自ρ为非零的特定总体时，会用到ρ≠0时r的检验方法。由于在这种情况下，r的样本分布不是正态，而是有偏的，所以在进行检验之前，需要将r和ρ都坐fisher’s z变换。r转换为zr后，zr的分布我们认为是正态的，其平均数是zρ，标准误SEzr=1/(sqrt(n-3))。这样就可以进行用下面的式子做Z检验了：

Z=(zr-z)/sqrt(1/(n-3))。

可以从上面的两个计算公式看到，r的显著性水平与样本量有明确的关系。我们以常见的ρ=0的情况为例：在描述两组数据的相关时，有两种极端结果a. r=0.06, p=0.05; b. r=0.5, p=0.5. 之所以存在这样的问题，是因为a情况有1000s的样本量；而b情况仅有寥寥几个样本照成的。这样看p看上去更可信一些（r的大小反映的是样本中两个变量之间的关系，但是p则反映的是总体中是否存在这种关系的可能，这样理解，在我们疑惑“哪个更可信时”其实我们的意思是“哪个更能说明总体中两个变量的关系？”，故而根据p判断更具说服力）。

还是上面的例子，a和b两种情况，哪种更相关？如何解释？

上面的问题集中在两个极端上，即相关显著，但是相关系数很小，甚至趋于零；另一端是相关系数很大，但是不显著。解决这个问题的方法即相关系数差异的显著性检验，这是实践中常碰到的问题。分两种情况：A. 两个相关系数r1和r2分别来自两组独立的样本；B. r1和r2来自同一组样本。

对于A情况，分别对r1和r2进行fisher’s z变换得到zr1和zr2，这样zr1-zr2符合正态分布，标准误是SE=sqrt((1/(n1-3))+(1/(n2-3)))。然后采用下面的公式做z检验即可：

Z=(zr1-zr2)/sqrt((1/(n1-3))+(1/(n2-3)))

这里有一个web的应用可以完成[Calculation for the test of the difference between two independent correlation coefficients](http://www.quantpsy.org/corrtest/corrtest.htm)。

对于情况B，采用r12-r13检验ρ12-ρ13的差异是否显著，如重新修订的问卷与校标的相关是否显著大于修订前问卷与校标的相关（同一批被试上）。可以分别计算r12 r13和r23，然后采用下面的公式计算：

T=(r12-r13)sqrt((n-3)(1+r23))/sqrt(2(1-r12^2-r13^2-r23^2+2r12r13r23))

显著性检验必要吗？

有人说”如果相关系数是从small sample size得到的，你需要在r值后面跟上p”，这个很好理解，应为显著性与样本量存在必然的关系。但是如果是大被试量呢？举个例子很直观的例子，如果我们研究人的两种认知行为之间的关系，世界上所有的人都参与了测试，那么我得到的r就是总体的相关程度，这时候就没有必要做显著性检验得到p。那么样本量大到什么程度就没有必要做显著性检验了呢？这个问题留到后面探讨。

From Correlation to Causality？

相关不是因果，要想从相关得到因果关系，一种可能的增强信心的方式是较强的先验假设，（时序先后也可以在一定程度上说明相关暗示的因果关系，但是同样需要较强的先验）；

![correlation2](/images/post_images/correlation.png "correlation")

画外音：相关可以很弱的implied因果关系，但是从相关到因果，需要其他证据(数据或理论假设)的辅助。

其他

相关最适用与线性关系，对于曲线的关系可以用多元回归解决；相关仅适用于连续变量，且数据的大小是有意义的，对于纯的分类数据categorical data则不适用correlation。

参考：

[相关系数及其显著性水平](http://bbs.pinggu.org/thread-425060-1-1.html)

[相关系数的显著性检验](http://www.mipang.org/blog/403792.4b3.htm)

[相关系数显著性检验表](http://hi.baidu.com/krcat/item/1183b28c2ad183834414cfc4)

[Correlation](http://www.surveysystem.com/correlation.htm)

[Calculation for the test of the difference between two independent correlation coefficients](http://www.quantpsy.org/corrtest/corrtest.htm)

http://imgs.xkcd.com/comics/correlation.png