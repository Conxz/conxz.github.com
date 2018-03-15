---
title: 学术发表用高质量图片保存
date: 2018-03-15 22:30:59
tags: [open science, publication, paper]
category: OpenScience
---
在学术论文发表中，不同期刊对图片质量的要求通常有所差异，比如，并不是每个期刊对图片质量的要求都是300ppi。在学术写作中，关于如何保存高质量图片有一些小trick，写在这里方便查询。

准备工作：
- **期刊对分辨率的要求**：一般情况下300ppi可以满足出版要求，不同期刊针对不同类型的要求有所不同。通常对统计作图的线条或柱状图的要求高一些（比如1000ppi），对图片要求低一些（比如300ppi或600ppi）。
- **字体大小**：字体不要太小，一般要求图中字体不能小于6点（point或pt）。72 点等于 1英寸，1 point 约等于0.353 mm，6ponit不到2.12mm。
- **图片格式**：通常期刊接受TIFF文件，这个可以通过PPT直接导出（注意设置ppi），或者R直接保存（注意ppi），或者从Photoshop或Illustrator导出（同样需要注意ppi的设置）。更推荐的方式是直接保存矢量图，比如采用R保存svg或pdf，或Illustrator保存pdf或eps。
- **图片尺寸**：在准备图片时，需要注意图片出版时的大小。有些期刊对图片的尺寸要求不严，但是有一些期刊由于涉及到排版问题，对图片要求相对严一些。通常学术论文采用双栏排版，图片可以是单栏（9cm），一栏半（14cm），或两栏（19cm）（图一）。因此考虑到排版需要，期刊对图片的宽度有特定要求，比如PNAS要求1栏图片的宽度为8.7cm，1.5栏图片的宽度为11.4cm，而2栏图片的宽度为17.8cm。

![论文图片尺寸](/images/post_images/scifig.png)

**推荐参数：TIFF图片分辨率600ppi（统计图1000ppi），或直接保存矢量图（比如pdf格式） + 图片宽度8.7/11.4/17.8cm + 最小字号6-8**

---
**R/RStudio:**
保存TIFF格式图片

*tiff(file = "C:/test1.tiff", res = 600, width = 11.4, height = 15, units='cm', compression = "lzw")
plot(1:22, pch = 1:22, cex = 1:3, col = 1:5)
dev.off()*


保存PDF格式

*pdf(fig_file, width = 11.4, height = 15, pointsize = 8)
plot(1:22, pch = 1:22, cex = 1:3, col = 1:5)
dev.off()*

---
**Illustrator：
**
设置图片尺寸：File > New...，根据需要设置宽度Width，注意单位Units
设置导出非矢量图时的分辨率：Effect > Document Raster Effect Settings，Color Mode选RGB，Resolution根据需要设定。
导出TIFF：File > Export...， 选择TIFF格式保存。
保存PDF或EPS：File > Save As...，选择相应格式并保存。
其他：
如果发现图片边框空白太多，可以采用Illustrator截取多余的部分：File > Document Setup ...，点击Edit Artboards，然后可以通过拖拽虚线方框设定感兴趣的区域。

---
**PPT + Photoshop：
**
此法不推荐，虽然是我之前最常用的作图方法。
PPT导出TIFF图片（注意保存前，需要通过File > Options > Advanced > Image Size and Quality设置导出图片的分辨率为330ppi，并勾选‘Do not compress image in file’）
此后，在Photoshop中打开图片，然后Image > Image Size...，设置Document Size下的Width和Resolution到相当的参数（可选项：取消勾选‘Resample Image’）。
最后保存图片为TIFF格式。

---
**PPT + Illustrator：
**
采用PPT设计图片排版，之后将各元素一起复制粘贴到Illustrator。同样注意，在ppt中设计排版之前，设置Slide Size为相应的尺寸（Design > Slide Size > Custom Slide Size...）。之后的操作在Illustrator中完成。

当然，所有排版、设置和保存等步骤都可以在Photoshop或Illustrator中完成。

ps：关于修改图片分辨率，这个漫画的右上角是现实。
http://www.phdcomics.com/comics/archive/phd040609s.gif
