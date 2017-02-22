---
layout: post
title: "由一篇JN上的文章想到的"
date: 2013-11-14 12:52
comments: true
categories: BrainResearch
tags: [reading, mvpa]
---
这周组会我报告的是薛贵老师发在JN上的一篇脑结构预测reading ability的文章。起初选择该文章是出于以下两点考虑：1. 近期做个体差异的工作相对多一些，在分析方法上可能有所借鉴；2. 写作思路上的借鉴。

这篇文章内容大致如下：

在以往存在功能和结构成像技术研究reading的加工机制和个体差异的神经基础的背景下，作者提出已有研究存在两个问题，一方面往往采用单一的reading task，而reading ability是一个复杂的能力，由多个成分构成；另一方面样本量相对偏小。然后作者针对这两点，展开自己的研究。这篇文章涉及到7个不同的reading task，作者首先做了因素分析找到其中的3个成分，并分别命名为`phonological reading`，`form-sound association`和`naming speed`。然后采用fMRI研究中常用的MVPA的方法采用VBM的结构数据分别对3个成分进行预测。最后也采用传统的一元分析方式与MVPA的结果做了简单的对比。
<!--more-->
值得学习的地方：

1. 关于为什么采用脑结构数据的引入。这个问题我们之前也有考虑，我之前能想到的只是以往研究发现脑结构的个体差异有意义，可以预测一些行为上的个体差异；这篇文章提出另一个观点值得我们借鉴：`Compared with functional
imaging, the anatomical approach requires less participant cooperation, and is most cost-effective and less contaminated by performance differences, providing an ideal tool for a large scale study of participants with various ages and reading abilities.`

2. 关于VBM研究不能明确因果关系的限制，这种不确定方向的问题可以采用类似的方式写一下。`our results could not pinpoint whether the observed correlations were caused by preexisting individual differences (Xue et al., 2006b; Wong et al., 2011) or brain plasticity during language learning (Mechelli et al., 2004; Carreiras et al., 2009). Future longitudinal studies might help to address this issue (Hoeft et al., 2011).`

最后吐槽一下这篇文章里的bug：

1. 作者说他们采用的MVPA的方法相对于传统一元分析要敏感一些，但是没有给出量化的比较。实际上，文章的MVPA的结果并没有做多重比较校正，而一元的分析则采用了相对严格的FDR校正。这样，一方面，拿一个没校正的结果和一个严格校正的结果做对比，不能说明问题；另一方面，一个未校正的结果为什么可以发表，这个问题值得我们思考。(说到这里，突然想到了那篇Culture and Brain上的关于snp的奇文，感兴趣的可以自己找来看看)

![Multiple Comparison Correction](/images/post_images/mcc.jpg "Multiple Comparison Correction")

2. MVPA的结果包含了小脑，而一元的结果则把小脑忽略了，作者没有明确提及这一操作，但是，我想如果不是“学生疏忽”的话，背后应该有故事。

文献：
*Decoding the Neuroanatomical Basis of Reading Ability: A Multivoxel Morphometric Study. The Journal of Neuroscience, 2013.*
