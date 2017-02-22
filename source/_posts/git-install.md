---
title: CentOS上非root安装git
date: 2013-05-14 08:10:27
tags:
---
CentOS 6之前yum源中没有git，只能自己编译安装。下面是简单的记录：

wget http://www.codemonkey.org.uk/projects/git-snapshots/git/git-latest.tar.gz

tar xzvf git-latest.tar.gz

cd git-2013-5-14 ＃今天这个是最新版本

autoconf

./configure --prefix=/nfs/j3/userhome/xxx/opt/

make

make install


试一下是否安装成功

git –version
