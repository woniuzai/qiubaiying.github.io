---
layout:     post   				    # 使用的布局（不需要改）
title:      tensorflow移植到android平台 				# 标题 
subtitle:    #副标题
date:       2017-11-07 				# 时间
author:     BY 						# 作者
header-img: img/post-bg-2015.jpg 	#这篇文章标题背景图片
catalog: true 						# 是否归档
tags:								#标签
    - tensorflow
    - android
---

# 编译tensorflow的android demo
## 环境准备
windows7 64bit,官网上有两种方式使用demo，我选择了推荐的IDE方式，使用了android studio。本人旧版2.0老是报错，后来更新到了3.0的as。[官方教程链接]https://www.tensorflow.org/mobile/android_build

### 获取tensorflow源码
    
    git clone https://github.com/tensorflow/tensorflow
    
### 使用as打开tensorflow的demo
这里as会报出各种依赖等的问题，需要安装一堆的包，需要翻墙可以连接到google的代码库（as可以设置http代理），终于gradle sync成功了，注意在bulid.gradle文件中修改
    // set to 'bazel', 'cmake', 'makefile', 'none'
    def nativeBuildSystem = 'none'
没有错的话，可以成功安装到手机了。

## 问题解决
1.更新as到3.0
在windows7 64位的操作系统下，之前安装了android studio2.0，后来
