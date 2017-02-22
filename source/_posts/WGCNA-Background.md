---
title: WGCNA Background
date: 2017-02-08 20:38:27
tags: 
---
WGCNA是Weighted Gene Co-expression Network Analysis的简称，其从网络连接的角度出发，考查基因之间的交互。该方法的提出背景是通过微阵列（microarray）实验可以获取的信息远多于仅得到一组差异表达的基因（differentially expressed genes）。基于微阵列microarray数据，我们可以通过计算基因表达模式（gene expression profiles）之间的相关来考查不同基因之间的交互。采用WGCNA方法，可以从数千基因的表达水平数据中识别可能具有临床价值的基因模块（gene modules），并最终采用模块内连接（intramodular connectivity）和基因-特质相关（gene significance）来发现某些疾病通路的关键基因，用于进一步验证。

WGCNA很好地解决了传统微阵列数据分析（microarray data analysis）中的多重检验问题（multiple testing problem）。与将数千基因的表达水平分别和样本的某一特质进行关联分析的做法不同，WGCNA方法重点关注少数模块（modules）与样本特质之间的关联。为此，该方法计算特征基因关联（即样本特质与模块特征基因分数之间的相关），并针对每个模块（module）得到相应的p值。

此外，虽然一般还会将得到的模块与本体ontology信息相关联，以探索模块的生物学意义，但是这并非必须。因为模块可能对应了生物学通路，关注模块内的核心基因（intramodular hub genes）也意味着一种基于生物学考虑的数据降维策略。因为模块内核心基因的表达模式是高度相关的，一般会得到许多候选生物标记（biomarkers）。虽然这些候选基因在统计上是等同的，但他们在生物学意义或临床应用上确可能不同。基因本体ontology信息可以在进一步筛选模块内基因中发挥作用。

在实际的WGCNA分析中，涉及到的网络分析概念与脑网络分析中的概念是类似的。比如共表达网络（co-expression network）即由基因作为节点，基因表达水平的相关值作为连接而构成。模块（modules）即一组高度相关的基因。度（degree）和模块内度（intramodular degree）也是类似的概念，不过在WGCNA中也会用connectivity一词代替degree使用。模块特征基因（module eigengene）被定义为给定模块的第一个主成分，是该模块最具代表性的表达模式。特征基因相关（eigengene significance）即模块特征基因与某一样本特质之间的相关值。另一个相关的概念是模块归属（module membership），也称基于特征基因的连接，即某个基因的表达模式与某模块特征基因之间的相关；因此该值越大，表示该基因可能归属这个模块。核心基因（hub gene）是高度连接的基因（highly connected genes）的别称。
此外，基因相关（gene significance）即基因表达模式与某样本特质之间的相关，一般相关值越大，表示该基因越重要，比如它可能参与编码通路归属（pathway membership）等。有时候也用负log（p）来量化这个基因相关（gene significance）。模块相关（module significance）的定义是该模块中所有基因相关绝对值的均值。当基因相关是基于基因表达模式与样本特质之间的相关值时，该测量与模块特征基因和样本特质之间存在高相关。

下图是一个典型的网络分析流程。

![wgcna pipeline](/images/post_images/wgcna.png "WGCNA")

1. 构建基因共表达网络。基本目的是充分利用基因间的交互模式；采用相关系数作为共表达的测量。
2. 识别模块。基本目的是模块分析；可以采用层次聚类（hierarchical clustering）或动态树切分（dynamic tree cut）实现。
3. 将模块与外部信息关联。其中外部信息包括基于阵列的临床数据（clinical data），多态性数据（SNPs）和蛋白组数据（proteomics）；基因信息包括ontology和功能富集（functional enrichment）。基本目的是发现具有生物学意义的模块。
4. 研究模块之间的关联。基本目的是生物数据降维，并提供系统水平的视角（system-level view）；采用eigengene网络实现。
5. 最后发现感兴趣模块的关键驱动子（key drivers）。基本目的是实验验证并明确生物标记（biomarker）；采用的手段可以是模块内连接（intramodular connectivity）以及因果检验（causality testing）。

参考来源 [WGCNA: an R package for weighted correlation network analysis](https://labs.genetics.ucla.edu/horvath/CoexpressionNetwork/Rpackages/WGCNA/)