---
layout: post
title: "deploy时[non-fast-forward]reject问题解决方案"
date: 2014-04-12 22:49
comments: true
categories: Tools
tags: blog
---
Github+Octopress rake deploy时[non-fast-forward]reject问题解决方案

好久没更新blog，今天写好文deploy时发现报错：

	! [rejected]        master -> master (non-fast-forward)

在网络google了半下午，终于找到了解决方案：

更换目录，并更新：

	cd octopress/_deploy
	git pull origin master

跳出目录，重新deploy：
	cd ..
	rake deploy

问题解决。
<!--more-->
参考：
http://stackoverflow.com/questions/17609453/rake-gen-deploy-rejected-in-octopress

