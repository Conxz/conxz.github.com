---
title: volume的统计结果mapping到surface
date: 2012-07-23 19:53:27
tags:
---
前一段折腾了一下用caret将基于volume的统计结果mapping到surface上显示的事情，虽然当时查了一堆材料，流程走通了其实很简单。

surface显示相对于volume的好处就不说了，mapping到surface这个活儿也可以用tksurfer来做（大家之前用过的），不过视觉效果真心不如caret。

简单截了一个动画，大家需要时可以试一下，点我[链接失效]下载动画，用QQ player播放即可。

注意在练习之前需要一些准备工作：

1. 安装caret的计算机（linux、window、mac均可）；

2. 标准头的spec文件，这个直接从caret的官网下载即可，点我下载；

3. 随便一个基于volume的统计结果。

下面附上一张caret显示的效果图(navigation相关脑区空间分布概率图)：

![surfacefig](/images/post_images/vol2surf.jpeg "Volume2Surface")