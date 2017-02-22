---
layout: post
title: "动态网络矩阵 可视化"
date: 2013-12-19 13:08
comments: true
categories: BrainResearch
tags: brain network
---
在过去的几年里，网络分析方法从社交网络辗转到人脑网络，火爆一时，也饱受诟病。不管怎样，网络分析方法确实给我们提供了一个新的观察和认识人脑的方式。

科学发展往往遵循一个“从一元到多元，从静态到动态”的演变规律，如今，研究者也不再满足分析一个单独的静态网络，而是开始试图从动态变化的视角观察人脑网络。这个动态可是短时的（比如一次扫描中人脑网络的变化），也可以是长时的（比如是在一天中不同时段人脑网络的变化，甚至是人的一生中脑网络的动态变化）。

通常，研究者采用一个矩阵来存储一个网络，矩阵中每个行或列表示一个node，而每个cell的值表示相应的两个node的连接强度。

![网络矩阵](/images/post_images/mat_imshow.jpg "网络矩阵")
<!--more-->
用python可视化一个矩阵可以采用如下方式：

	plt.imshow(dat, origin='lower',interpolation='nearest', cmap=plt.get_cmap('jet'))
	plt.show()

如何可视化一个网络的动态变化呢？一种方式可以采用matplotlib提供的animation工具。举例如下：
	import matplotlib.animation as animation
	for sess in sesslist:
    	print 'Adding ', sess
    	sessdir = os.path.join(datadir, sess)
    	mat_dat_file = os.path.join(sessdir, mat_dat)
    
    	dat = np.load(mat_dat_file)
    	dat = dat['im']

    im = plt.imshow(dat, origin='lower',interpolation='nearest', cmap=plt.get_cmap('jet'))
    ims.append([im])
    
	ani = animation.ArtistAnimation(fig, ims, interval=50, blit=True, repeat_delay=1000)
	plt.show()

