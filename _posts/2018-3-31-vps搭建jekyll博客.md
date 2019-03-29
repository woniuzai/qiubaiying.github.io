---
layout:     post   				    # 使用的布局（不需要改）
comments: true
title:		vps利用jekyll搭建静态博客 				# 标题 
subtitle:    #副标题
date:       2018-3-31 				# 时间
author:     woniuzai						# 作者
header-img: img/post-bg-2015.jpg 	#这篇文章标题背景图片
catalog: true 						# 是否归档
tags:								#标签
    - jekyll
    - blog
---

# vps搭建jekyll
直接利用apt-get install jekyll安装，然后利用jekyll build生成静态页面。

# nginx配置
配置sites_enable里面的default配置，指向生成静态页面的博客路径。



