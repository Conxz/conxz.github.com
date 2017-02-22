---
title: 读《复杂数据统计方法》之初见
date: 2013-02-22 20:10:27
tags:
---
书的第一章讲到，统计可以定义为‘收集、分析、展示和解释数据的科学’，也称‘数据科学’。

书题中提及的‘复杂数据’并没有确切的定义，但是却与统计学发展的不同阶段有密切联系。早期人们获取的数据的量和复杂程度要远逊于big data盛行的今天，加上计算资源的限制，人们更倾向于采用基于诸如独立同正态分布之类的数学假设的数据分析方法，即‘模型驱动’的研究方法；后来随着计算机的发展，科学家可以接触到的计算资源也不断增加（比如我们实验室自己搞的SGE并行计算平台，以前哪有想过心理学家会需要用这个呢，哈哈），更多的科学家开始接受以数据为主导的研究方式，特别是决策树、boosting、随机森林和SVM等大量算法模型的相继出现基本宣告了传统模型主导的数据分析时代的终结。

对于模型驱动和数据驱动的区别，作者提到一个很关键的一点，即对结果的评价。传统的模型驱动的研究方法中一般采用假定分布所得到的p值来描述；而数据驱动则是采用CV的方式描述（即用没有参加建模训练的测试集数据的误差来描述）。

另外，作者提到一点感想，研究者应该会有所感触。作者讲，‘现在，…，如果不会计算机编程，也不与编程人员合作，则不会产生任何有意义的成果’。这句话虽说是针对统计学家的，但是在学科间不断交叉的今天，各个领域确实越来越需要熟悉甚至精通数据分析方法，而非计算领域研究者自己再去学习数据分析方法大多数情况下却又不可能，或者荒废时间，所没有必要。这也就导致目前的状况下，不同领域间研究者合作的必要性。这样研究者既可以专注自身的领域，又可以提高科学研究的效率，何乐而不为呢。（于是taobao上出现了大量提供数据分析服务的小店J）

这本书结合实例讲解数据分析方法，工具用常用但是万能的R。第一章的最后作者推荐了两本R语言的书（Statistics with R和Modern Applied Statistics with S）和一个软件（RStudio）+。

+ R软件用的是S语言。