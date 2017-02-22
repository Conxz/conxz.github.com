---
title: 配准位移有信息么？
date: 2012-10-09 23:10:27
tags:
---
今天看发布TBSS的2006的一篇文章，看到一个很有意思的参数，nonlinear displacement。看上去配准的时候位移应该是没有什么意义的，但是这其中似乎真的有一些信息等着我们挖掘。

Smith et al., 2006 为了identify the target for alignment，考查了summary nonlinear displacement scores (Fig. 7)。For each target subject, a column of scores is shown; each score represents the root mean square displacement (across all brain voxels) for the nonlinear component of the alignment of any given subject to the target subject.

![displacement summary](/images/post_images/registration.png "displacement summary")


[前20为control，后面为病人。The bottom row summarises the target subjects; the first 20 subjects are the controls, and the final 13 are ALS patients, with clearly greater structural variability than the control group.]

结果发现，Note also the greater variability within the patient group than within the control group. The means of the two groups, however, are not significantly different.

Nonlinear displacement 看上去是一个很有意思的参数。那么如何计算得到呢？

--fout output type of fnirt

the --fout is in fact the displacement in millimeters of the tranformation.

可能的应用：

可以考虑采用该方法剔除outlier；考查displacement的生理意义？以及采用总体中样本相互配准得到的displacement对被试进行分类？以及考查displacement的空间分布及其意义。

如下是将某被试的FA数据配准到标准空间的displacement的空间分布，可以看出displacement较大的地方主要在枕叶和顶叶。当然，这只是一个现象，不代表统计意义。

![displacement map](/images/post_images/registration2.png "displacement map")
当然，这个空间分布可能和被试躺的位置有关系。。。
