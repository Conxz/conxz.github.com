---
title: Parcellation display with the same color using freesurfer
date: 2017-04-01 13:39:55
categories: Tools
tags: freesurfer
---
Two methods for displaying ROI analysis results with brain parcellation in FreeSurfer. 

1. Solution #1 using R. The R code can be found [HERE](https://github.com/Conxz/vis/blob/master/CreateFSLUT.r). After running the code, a configration file (like [THIS](https://github.com/Conxz/vis/blob/master/lh-Area-ColorLUT.txt)) can be obtained. Then, by following the instructions at the end of the R code, you can have the display with tksurfer. 
![surf vis 1](/images/post_images/vis_fig_r_lateral.png "vis1")

2. Solution #2 using Matlab. The Matlab code can be found [HERE](https://github.com/Conxz/vis/blob/master/vis_pre_fs.m). Note that it depdends a matlab function fron Freesurfer 6.0. After running the code, a mgh file can be obtained for the visualization with tksurferfv. 
![surf vis 2](/images/post_images/vis_fig_m.png "vis2")



Note that:
- Both methods are based on a csv file, like [THIS](https://github.com/Conxz/vis/blob/master/vis_example.csv). 

- Different options for the brain display: inflated/orig/smoothwm/white/pial/sphere