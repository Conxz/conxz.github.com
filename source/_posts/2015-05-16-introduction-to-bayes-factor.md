---
layout: post
title: "Bayes Factor (简述贝叶斯因子) [2]"
date: 2015-05-23 22:53
comments: true
categories: Methods
tags: bayes factor
---
**Bayes factor的几个应用途径**

1. 作为一种统计推断的方法，Bayes factor首先可以**用来代替p值**（一般根据p<0.05来决定拒绝虚无假设（null hypothesis, H0），接受备择假设（alternative hypothesis, H1））来确定备择假设是否可靠。这里的H0和H1即两个不同的模型，计算Bayes factor（![](/images/post_images/bayes_2.jpg)）。同样，如果计算得到的Bayes factor大于3，即数据x支持H1的概率是数据x支持H0的3倍以上，则被认为有足够的证据说明模型H1的正确性（类似根据p<0.05做出的结论）。

2. 采用p值做统计推断时，一个常识是不可以简单地使用p>0.05作为H0成立的证据，即研究者不可以简单地做接受H0的结论（因为导致不显著的原因除了“H0成立”之外，还有比如样本不足，不够敏感等的影响；因此，如果非要做结论，一般需要结合power或effect size的信息来辅助进行）。而Bayes factor在这种场景中却派上了用场。如果统计结果显示上面计算得到的Bayes factor小于1/3，甚至更小，研究者就有足够的信心来接受H0模型。因此，**Bayes factor可以方便研究者确定“没有结果”的可靠性**，用于理论检验和构建。

3. 个人认为Bayes factor还可以在另一个地方派上用场，即关于大样本研究中发现的效应值小（small effect size）的问题。随着数据采集条件的完善，行为神经科学中大样本的数据不断普及。同时研究者也发现，在大样本的数据统计中，0.2左右的效应量变得异常普遍，于是一些没有相关经验的审稿人（reviewer）便通常会提出类似“the amount of variance that impulsivity accounted for was a mere 2%”的问题，并质疑结果的可靠性。这个时候reviewer一般会要求做分半，进一步验证结果的可靠性。Bayes factor提供了另一个角度来**展示结论的可靠性**。以我自己的研究为例（Kong et al., PLOS ONE, 2014），我们发现被试在核磁扫描中头动（In-scanner head motion）的大小和被试的自我控制特质（Self-control impulsivity）存在显著关联，但是相关系数只有0.14（p=0.001），这时，可以计算该分析的Bayes factor发现BF = 9.1，因为大于3，可以认为有足够的证据确信头功和被试的自我控制特质之间存在的关联。

参考文献：

- Kong X-Z*, Zhen Z*, Li X, Lu H-h, Wang R, Liu, L, He, Y, Zang, Y-f, Liu, J. (2014) Individual Differences in Impulsivity Predict Head Motion during Magnetic Resonance Imaging. PLoS ONE 9(8): e104989. doi:10.1371/journal.pone.0104989.

<!--more-->
