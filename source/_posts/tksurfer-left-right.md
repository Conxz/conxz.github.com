---
title: 使用tksurfer可视化左右脑颠倒问题
date: 2013-07-01 20:10:27
tags:
---
Tksurfer是freesurfer中可视化surface结果的很方便实用的工具，命令举例如下：

tksurfer fsaverage lh inflated –overlay./fwhm10lh/c1.contrast/sig.mgh

即将统计分析结果sig.mgh左脑部分映射显示到“吹起”（inflated）皮层（以fsaverage为背景）上。

正常情况下，应该把左脑的结果映射到左侧脑皮层上。但是做影像处理的总会碰到各种意想不到的灵异事件，我得到的map结果确实这样的：

![tksurfer1](/images/post_images/tksurfer1.jpeg "tksurfer1")

这是要闹哪样啊!!!

明明选择的是lh，为什么显示到rh了，更诡异的是看看color bar，这是什么情况。在仔细核对结果后发现，map上去的结果确实是左脑的激活结果。

结合以前的经验，color bar应该是在右下角显示的，猜想是“上下镜像”了，于是试着做了翻转，好吗，这回还算靠谱。

![tksurfer2](/images/post_images/tksurfer2.jpeg "tksurfer2")

这不就是lh的效果嘛，这回算是正常了。

问了freesurfer的开发者，他们表示“that is something I have never seen before”，根据他们的建议，检查了freesurfer的版本和系统版本，并根据系统版本重新安装了相应版本的freesurfer，不过问题依然存在。

经过这么几天的折腾，问题暂时没有解决，不过暂时有了临时解决方案：自己上下镜像一下。

目前猜想可能是由于系统升级导致的错误，具体暂未找到完美解决方案。