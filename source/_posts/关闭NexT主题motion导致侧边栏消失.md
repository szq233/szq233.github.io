---
title: 关闭NexT主题动画导致侧边栏消失
date: 2021-04-30 02:32:36
tags: [Hexo, NexT]
categories:	[Hexo, NexT]
---

*概要：关于Hexo的NexT主题关闭motion动画导致侧边栏消失的解决方法......*

###### <!--more-->

##### 起因：

最近上手Hexo搭建博客，顺利搭建博客并一眼相中NexT这类简约风格的主题样式。

最初，NexT主题因为搭载的 [https://theme-next.js.org/animate](https://theme-next.js.org/animate)的CSS动画引擎，第一眼那丝滑的动画确实特别惹眼，但由于个人喜好极速简约，便在网络上搜索关闭NexT主题过渡动画的方法，按网络上说法将主题根目录下_config.yml文件的`motion： enable：true`修改为`enable：false`，确实完成了动画的关闭，但拥有小部件和头像功能的侧边栏消失。

花了段时间找问题，在打开浏览器调试功能时，发现.sidebar元素被赋予了`visiblity：hidden`属性，在修改为`visiblity：visible`后，侧边栏再次可见。于是尝试找样式源文件，最终解决问题。

##### 解决方法：

因为我用的NexT主题的Pisces的scheme，其他类型的可以参照尝试解决，找到主题文件夹如下图路径中的_sidebar.styl文件，打开该文件。

![](03.png)

搜索visibility，将visibility: hidden;修改为visibility: visible;

![](04.png)

保存，执行hexo cl、hexo g、hexo d稍微等待一会，刷新博客，发现侧边栏可以正常显示