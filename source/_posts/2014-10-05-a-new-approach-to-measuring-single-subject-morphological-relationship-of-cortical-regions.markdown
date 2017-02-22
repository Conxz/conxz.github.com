---
layout: post
title: "一种基于单被试MRI脑影像量化脑区间连接的新方法"
date: 2014-10-05 09:53
comments: true
categories: BrainResearch
tags: brain network
---
目前研究者普遍认为，人类复杂的认知过程并不能由单独的某个脑区完成，而是依赖多个脑区间的协调工作。因此，考查脑区间的关联对进一步深入理解大脑的工作机制有极为重要的意义，也是近年来脑区连接和脑网络成为脑科学研究热点的主要原因。

目前通过核磁共振成像技术采集的脑数据构建脑区连接和脑网络主要有以下几种方式：基于DTI数据量化脑区间白质纤维连接进而构建脑网络；基于fMRI数据通过脑区间BOLD信号的波动共变量化功能连接进而构建脑网络；通过MRI数据通过脑区测量（如皮层厚度、体积等）在被试间的共变量化结构连接进而构建脑网络。其中，前两种方法都可以实现对单个被试网络的构建，而已有基于MRI数据量化连接的方法主要基于一组被试，无法实现对单个被试中脑区连接的量化。

但是，构建单个被试脑区连接在实际应用中是极为需要的。比如通过构建了单个被试的脑区连接和网络，可以提高对疾病的个体差异的认识，并进而促进未来基于核磁数据的诊断。[这个研究](http://www.sciencedirect.com/science/article/pii/S0165027014003203)旨在提出一种基于MRI脑结构数据量化脑区间关联的新方法。该方法可以总结为一下三步：

1. 计算脑中每个体素的局部形态学特征；
2. 脑区分割，并估计每个脑区形态学特征的分布；
3. 通过估计两两脑区的形态学特征的分布来量化两两脑区间的关系，即脑区连接。

下面是该方法的流程示意图。

[X.-z.  Kong  et  al.  /  Journal  of  Neuroscience  Methods  237  (2014)  103–107  105](http://www.sciencedirect.com/science/article/pii/S0165027014003203)

![DBIR](/images/post_images/dbir.jpg "DBIR")

<!--more-->

Highlights

- A new metric was proposed to quantify individual morphological relations of regions.
- The new metric is indexed as the similarity of different morphological distributions.
- We estimate the morphological distribution from individual MRI image.
- The metric seemed to have potential application to individual differences studies.

*注：未订阅免费下载连接（2014年11月17日前有效） [点此下载 http://authors.elsevier.com/a/1PmxUbXTOZ4e3](http://authors.elsevier.com/a/1PmxUbXTOZ4e3)*
