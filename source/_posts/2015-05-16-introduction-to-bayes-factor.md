---
layout: post
title: "Bayes Factor (简述贝叶斯因子) [1]"
date: 2015-05-23 22:53
comments: true
categories: Methods
tags: bayes factor
---
**Bayes factor是什么？**

最近读文献，发现研究者开始使用Bayes factor来说明一些问题（比如Russell实验室的新文Julian et al., 2015），看来大势所趋了，需要学习一下。

Bayes factor（贝叶斯因子）被用来描述一个理论优于另一个理论的相对确证性（ the relative evidence for one theory over another ）(Dienes, 2014)，采用数学符号表示即

![](/images/post_images/bayes_2.jpg)

其中，x为观测到的数据，H0和H1分别为两种理论或模型，p(x|Hi)表示Hi成立时，观测到x的概率，即x数据底层模型满足Hi的概率。实际上p(x|Hi)的一个常用的名字叫似然概率（likelihood），这样，Bayes factor因为由基于两个模型的likelihood的比值定义，也被称为似然比（likelihood ratio）。

因此，Bayes factor量化的就是数据x支持不同理论的确证性，换句话说，Bayes factor量化的是数据x支持模型A的概率是支持模型B的概率的倍数。为了使用方便，研究者给不同大小的Bayes factor打上了类似假设检验中“显著”“边缘显著”“不显著”的标签（Jeffreys H.，1939/1961）： 一般大于3或小于1/3被认为是实质性的证据（substantial evidence）；而1/3到3之间则被认为是较弱或有待验证的证据（weak or anecdotal evidence） 

参考文献：

- Julian et al. (2015). Place recognition and heading retrieval are mediated by dissociable cognitive systems in mice. Proc.Natl.Acad.Sci.U.S.A. www.pnas.org/cgi/doi/10.1073/pnas.1424194112

- Dienes Z. (2014). Using Bayes to get the most out of non-significant results. Front.Psychol. 5:781. doi:10.3389/fpsyg.2014.00781

- Jeffreys, H. (1939/1961). The Theory of Probability, 1st/3rd Edn. Oxford, England: Oxford University Press.

<!--more-->
