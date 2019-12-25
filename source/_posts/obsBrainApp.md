---
title: 记第一个Shiny应用obsBrain
date: 2018-12-27 21:05:11
tags: [R, shiny app, open science, data science]
category: OpenScience
---
Shiny是一项RStudio开发支持的交互式网页技术，基于此技术，可以用R语言相对轻松地实现交互式网页应用。由于其轻便、易学和交互式特点，该技术尤其适用于在学术发表的同时，交互式呈现数据科学分析结果，以方便读者更好地查看和理解研究方法和研究结果。
在以往自己的数据计算中，Python占了主导。不过从2016年下半年到现在的实验室之后，更多的时候采用R完成数据计算，深知其便捷性。期间对Shiny也有一些接触，不过属“点头之交”：大致晓得其基本功能，但没来得及深入学习。于是，趁着圣诞和新年假期，具体学了一下Shiny应用的实现，并结合目前的研究兴趣得到的第一个应用。
![obsBrain](/images/post_images/obsbrain.png)
<!--more-->
在这个应用中主要实现了一下几个功能：
- 可视化人脑基因表达的空间分布
- 汇集和展示ENIGMA多中心合作项目在多个研究中的主要结果（并呈现其与基因表达的空间相关分析结果）
- 提供一个方便使用的可视化工具

所有这些功能均基于FreeSurfer提供的Desikan–Killiany图谱（半脑分为34个脑区），这也是目前ENIGMA多中心合作项目使用最多的脑分割图谱。暂且将其命名为obsBrain，全称为Observatory of Brain。
该应用目前已发布到网络，可以通过如下链接访问:
https://conxz.shinyapps.io/obsbrain/
此外，所有数据准备和具体应用实现相关代码和数据均已发布在GitHub，可以通过如下链接访问:
https://github.com/Conxz/obsBrain

关于该应用的更多细节，可以参见README.md文件。同时欢迎感兴趣的同行联系交流（联系方式见README.md）。

