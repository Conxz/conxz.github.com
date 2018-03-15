---
title: unzip解压压缩包中指定的文件
date: 2017-12-13 07:14:26
tags: [data sharing, open science]
category: Tools
---
近年来，开放科学Open Science在学术圈得到越来越多的关注。在开放数据方面，研究者开始接受将采集的数据在线共享，同时越来越多的研究者开始基于在线共享的数据开展研究。

研究者通常以压缩包的形式将数据上传到网络。而在其他研究使用公开共享的数据开展研究时，由于通常情况下，该数据并非为其设计和采集，数据使用者需要将所有数据下载，并解压所有数据文件。有些时候（比如，用个人的笔记本下10几G的HCP数据），下载的压缩包本身就很大，如果全部解压，将会占用更多硬盘空间（然而，我硬盘空间不够解压所有数据了。。）。碰到这个问题，解决方案可以是将数据copy到另一台电脑或服务器，全部解压后，挑选需要的数据；另一个方案可以考虑选择性的解压一些需要的文件。本文就是笔者在使用HCP数据时，由于碰到Mac空间有限的问题，找到的解决方案。

以HCP1200的处理好的数据为例，HCP1200_Parcellation_Timeseries_Netmats.zip大概有13G，如果全部解压出来需要差不多相当的空间。而笔者只感兴趣其中的几个文件，于是想到应该有一种解压感兴趣文件的解决方案，比如称为“基于感兴趣文件的解压” FOI（Files of Interest）-based Unzip 哈哈。

- 通过下面一条命令可以查看压缩文件中的目录结构，但不做实际解压。这样可以从结果中挑选兴趣的文件。
`unzip -v HCP1200_Parcellation_Timeseries_Netmats.zip`

- 通过下面一条命令解压指定的文件。比如，这里我们感兴趣与scripts.tar.gz这个文件。
`unzip HCP1200_Parcellation_Timeseries_Netmats.zip “HCP_PTN1200/scripts.tar.gz”`

- 如果感兴趣于多个文件，可以重复2中的命令。此外，如果只是对其中的某个/些文件不敢兴趣，可以采用-x参数，以在解压时排除指定文件(们)。
`unzip -x file1 file2 file2 HCP1200_Parcellation_Timeseries_Netmats.zip`