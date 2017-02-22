---
layout: post
title: "对surface参数做配对T检验:以睡眠剥夺实验为例"
date: 2013-11-13 19:14
comments: true
categories: BrainResearch
tags: [freesurfer, paired t-test]
---
在脑科学的研究中，带有操纵的前后测实验相对于个体差异或组间比较的实验，分量要相对大很多。而前后测往往就涉及到统计上的配对T检验。下面以一个例子记录一下针对Freesurfer生成的surface上的参数做配对T检验（Paired T-test）的流程。一方面自己备查，另一方面也希望对有相同需求的同学有所帮助。

这是一个前后测的研究，中间睡眠剥夺约72小时，共8名男性参与测试。下面的分析旨在考查72小时的睡眠剥夺是否对被试的皮层厚度（thickness）产生了一定的影响。<!--more-->

首先设置Freesurfer的环境变量SUBJECTS_DIR到数据所在目录，确保Freesufer能通过该环境变量找到需要分析的数据，命令如下：
	export SUBJECTS_DIR=~/subj/
这一步使用的命令在不同的系统上有所差异，export适用于Centos，其他google一下即可。

接下来就开始正式的工作，我们第一步需要获取需要分析的数据（比如每个被试右脑（rh）的皮层厚度（thickness）数据），并存在某个文件中。下面以获取8个被试的前后测的rh的thickness为例。
准备一个文本文件`pairs.fsgd`，内容格式如下：

	GroupDescriptorFile 1
	Class Main
	Input SD0101 Main
	Input SD0102 Main
	Input SD0201 Main
	Input SD0202 Main
	Input SD0401 Main
	Input SD0402 Main
	Input SD0501 Main
	Input SD0502 Main
	Input SD0601 Main
	Input SD0602 Main
	Input SD0701 Main
	Input SD0702 Main
	Input SD0801 Main
	Input SD0802 Main
	Input SD0901 Main
	Input SD0902 Main

其中SD0101和SD0102分别是被试01的前后测编号，该文件主要用于通过下面的命令获取这些编号的thickness数据。

	mris_preproc --target fsaverage --hemi rh  --meas thickness --out rh.paired-diff.thickness.mgh    --fsgd pairs.fsgd --paired-diff

该命令会生成一个名为`rh.paired-diff.thickness.mgh`的文件，需要注意的是--paired-diff这个参数的指定，使文件`rh.paired-diff.thickness.mgh`中实际上是每个被试前后侧的差值，即SD0101-SD0102，SD0201-SD0202等。因此，上面准备的文本文件中，同一被试的前后侧一定要顺序一致，并保证连续。

接下来可以对生成的差异数据做一下平滑，以提高信噪比，不过这一步是可选的。
	mri_surf2surf --s fsaverage --hemi rh --fwhm 10 --sval rh.paired-diff.thickness.mgh  --tval rh.paired-diff.thickness.sm10.mgh

再接下来就可以针对平滑后的数据`rh.paired-diff.thickness.sm10.mgh`做统计了。首先需要准备两个简单的文本文件：`paired-diff.fsgd`和`mean.mtx`。文件`paired-diff.fsgd`的内容：
	GroupDescriptorFile 1
	Class Main
	Variables 
	Input SD01 Main
	Input SD02 Main
	Input SD04 Main
	Input SD05 Main
	Input SD06 Main
	Input SD07 Main
	Input SD08 Main
	Input SD09 Main
文件`mean.mtx`的内容：
	1

准备好这些文件，就可以进行统计分析了。
	mri_glmfit --glmdir rh.paired-diff --y rh.paired-diff.thickness.sm10.mgh --fsgd paired-diff.fsgd --C mean.mtx --surf fsaverage rh

统计结果会生成在rh.paired-diff目录下的mean目录中，可以通过tksurfer命令可视化查看统计结果。

	tksurfer fsaverage rh inflated -overlay rh.paired-diff/mean/sig.mgh

也可以进一步对结果进行多重比较校正，查看校正后是否还有幸存的cluster。
	mri_glmfit-sim --glmdir rh.paired-diff --sim mc-z 5000 2 mc-z.abs --sim-sign abs --overwrite

可惜这个数据没有发现睡眠剥夺对皮层厚度的显著影响，原因可能有如下几条：

1. 样本量只有8名，被试量太少；
2. 皮层thickness指标相对稳定，很难在较短的时间内发生变化；
3. thickness可能发生了变化，但是MRI的测量精度无法检测到这一变化；
4. 可能在其他参数或测量的指标上有所变化。

目前除了一篇in press的文章发现睡眠剥夺会影响丘脑volume外，暂时没有发现睡眠剥夺影响大脑结构的文献（小鼠或病人-正常人对照除外）。感兴趣的同学可以搞来试试，不过被试可就惨了点。毕竟，被剥夺了睡觉的权利不是什么好事情，甚至可能导致“屈打成招”，一样的道理，天天熬夜也不是什么好事情，最近有研究发现晚睡影响脑结构，也有最近的研究发现熬夜影响免疫力，总之熬夜不是好事情，好了，洗洗睡了吧。
