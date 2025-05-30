---
layout: post
title: Linux实验7
slug: linux7
date: 2022-05-19 16:55
status: publish
author: 华仔仔
categories: 
  - Linux
tags: 
  - Linux
excerpt: Linux实验


---



**实验目的和要求：**

1了解Linux文件系统2 可以根据proc文件系统获取系统信息

**实验条件：**

1、装有Linux操作系统的微型计算机；

## 实验过程

Linux上的/proc目录是一种文件系统，称为proc文件系统（虚拟文件系统），它存储内核状态信息，包括cpu、内存以及进程等信息。proc文件系统有很多优点：应用程序获取内核数据不用切换到内核态，增加了系统的安全性（像ps命令就是通过proc获取进程信息）；应用程序可以通过proc直接改变内核参数，这样不用重新编译内核就可以改变和优化内核行为。总之，proc为用户应用程序获取系统内部信息提供了一个安全、方便的界面。proc存在内存中，不占用外存。我们的实验是使用proc文件系统，来获取系统信息**。**

下面是/proc目录下的文件：

![](images/e6fd3531e42dc69feca833abe883f079.png)

**要求根据上述知识，结合课程内容完成一个查看cpu和内核版本信息以及启动时间的程序。**

**  
参考解答：**

**必要的头文件**

![](images/e41f32c3b67ee1d2ac4cb2939bcb0591.png)

**相关数据结构：**

![](images/2cd0dcb0770fef09d5e7e07a5b7658bc.png)

**  
参考代码：**

**系统负荷函数：**

![](images/1243d1c5ea3d48a54f520191212df50c.png)

**观察系统启动时间：**

![](images/52f3c52d2ab73e57ae30b7a4adb513e7.png)**预期实验效果：**

![](images/8812f164dbf6f223a14472238b3e401e.png)

## 实验结果分析

1、熟悉并记录命令执行结果。

2、写出自己的心得体会。3. 实验报告仅提供封面，不提供正文模板。实验报告要求如下：

1）至少包含实验过程、实验结果、选择部分度量项目对结果进行简要解释。

2）报告章节要组织合理。

**核心思想是：根据参考案例，结合教材，了解makefile。结合操作系统的知识，你能进一步的结合man手册计算出进程的运行时间吗？**
