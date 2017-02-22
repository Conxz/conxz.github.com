---
layout: post
title: "用Python获取命令行输出"
date: 2013-10-25 15:30
comments: true
categories: Tools
tags: python
---

<p>Python在慢慢成为脑影像数据处理中的主流语言。而在做脑影像处理时，不免有时候需要用到一些别人开发好的工具包，而这些包并不都是python包。比如对方采用C写好了算法，我们觉得这个算法很好，用在自己的数据上应该会有不错的结果。我在处理脑影像数据时遇到下面的情况：</p>
<p>需要用的工具包是C写的，那第一件事就是需要在运行该脚本的机器上重新编译该代码为可执行的程序，也就是用`make`了。</p>
<p>产生可执行文件后，在Terminal中执行测试，可以正常运行，发现结果以print到屏幕上的形式给出。</p>
<p>通常我采用python进行脑影像数据的读写，在读取数据后并进行一定的预处理后，需要循环调用上面提及的可执行程序，并获取其输出的结果。这时候如何来实现呢？显然，常用的'os.system()'是搞不定的，引起它只会返回程序的执行状态。下面是在网上查到的几种方案，尝试过都可以work。</p>
<!--more-->
下面是测试用的可执行程序的字符串。
	
	mmcmd = ' '.join(['MMxnyn', infile, str(kneig)])

方案一：

	import commands
	status, output = commands.getstatusoutput(micmd)
	mi = output
	
方案二：

    import subprocess
    res = subprocess.Popen(micmd, shell=True, stdout=subprocess.PIPE, 
            stderr=subprocess.PIPE, close_fds=True)
    mi = res.stdout.readlines()
	mi = float((mi[0].strip())) 
*注：这里只用到了可执行程序输出的第一行，并转成float型返回。*

方案三：

    import os
    p = os.popen(' '.join(['MIxnyn', zwspfile, str(Ndx), str(Ndy), str(N), str(kneig)]))
    mi = p.read()
    mi = mi.strip()

留案备查。
