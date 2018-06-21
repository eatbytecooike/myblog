---
title: go环境变量(ubuntu)
date: 2018-06-15 17:50:29
tags:
categories:
- golang
---
临时设置环境变量: 
	添加到PATH末尾: export PATH=$PATH:/1/2/3
	添加到PATH开头: export PATH=/1/2/3:$PATH

环境变量参数: (linux区分大小写)
	GOROOT: go语言的根目录，官方推荐目录是: /usr/local
	PATH: 环境变量中增加: $GOROOT/bin
	GOPATH: 工作区，可以有一个或多个，一般目录为: $HOME/golang/examplegos

示例: 
	export GOROOT=/usr/local/go
	export PATH=$PATH:$GOROOT/bin
	export GOPATH=$HOME/golang/examplegos

永久设置环境变量

对所有用户生效 编辑 /etc/profile文件
对单一用户生效 编辑用户目录下 .bash_profile文件

立刻生效: source /etc/profile 或者 . /etc/profile
(source命令也称为“点命令”也就是一个符号（.）.source命令通常用于重新执行刚修改的初始或文件，使之立即生效，而不必注销并重新登录。)
