---
layout: post
title: "From freesurfer labels to volumetric masks"
date: 2013-11-08 12:44
comments: true
categories: BrainResearch
tags: freesurfer
---
最近的工作涉及到获取两个脑区的mask：`Fusiform Gyrus`和`Entorhinal Cortex`。考虑到被试间的结构变异，决定采用Freesurfer针对被试的T1像分割的结果，其中主要涉及到recon-all这个命令。

在每个被试分割生成的结果中有两个分割方案，分别是aparc.annot[[图](http://surfer.nmr.mgh.harvard.edu/fswiki/CorticalParcellation?action=AttachFile&do=get&target=annot-desikan.jpg)]和aparc.a2009s.annot[[图](http://surfer.nmr.mgh.harvard.edu/fswiki/CorticalParcellation?action=AttachFile&do=get&target=annot-destrieux.jpg)]。查看一些材料后，发现在要获取的mask上，两个分割方案存在一些差别。其中，aparc.annot中有单独的Entorhinal Cortex，而在aparc.a2009s中则将其融合进了旁海马的结构中，这样为了获取Entorhinal Cortex，可以从aparc.annot中获取；这对Fusiform Gyrus，在aparc.annot中存在一个Fusiform Cortex，即包括了Gyrus和Sulcus的结构，而在aparc.a2009s.annot中则把Gyrus和Sulcus做了区分，这样Fusiform Gyrus就可以从aparc.a2009s.annot中获取了。

接下来简单的记录一下从label到mask的操作过程（以Entorhinal Cortex为例）：<!--more-->

首先将aparc.annot中的label分离开来。

	mri_annotation2label -–subject S0001 -–hemi lh -–outdir ./labels

接下来获取变换矩阵，这里以被试自己的结构像为目标（也可以功能像或者diffusion空间为目标）。

	tkregister2 -–mov rawavg.mgz -–noedit -–s S0001 -–regheader -–reg ./register.dat

然后就可以根据变换矩阵将某个label转换成指定空间的mask了。关于每个参数的意义可以查看mri_label2vol --help。这里简答说一下--proj这个参数，他后面的赋值的格式是type start stop delta，其中type可以是abs或frac。frac 0 1 0.1 可以得到相应label对应的所有灰质；而abs -3 -2 0.1 则可以得到灰白质交界面2mm之下的mask，这个mask的厚度是1mm。

	mri_label2vol -–label ./labels/lh.entorhinal.label -–temp rawavg.mgz -–subject S0001 -–hemi lh -–o lh_entorhinal.nii.gz -–proj frac 0 1 .1 -–fillthresh .3 -–reg ./register.dat

最后就可以采用可视化工具，比如fslview查看结果了。

参考链接：


1. [http://brainybehavior.com/neuroimaging/2010/05/converting-cortical-labels-from-freesurfer-to-volumetric-masks/](http://brainybehavior.com/neuroimaging/2010/05/converting-cortical-labels-from-freesurfer-to-volumetric-masks/)


1. [http://blog.sciencenet.cn/blog-70715-590312.html](http://blog.sciencenet.cn/blog-70715-590312.html)
