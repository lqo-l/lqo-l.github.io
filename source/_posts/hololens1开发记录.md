---
title: hololens1开发记录
tags:
  - hololens1
  - AR
date: 2024-04-13 08:43:06
categories:
cover: img/cover/24-4-13.jpg
top_img: img/top/24-4-13.jpg
description:
copyright: false
---
# 前言
&emsp;&emsp;最近irtoa在利用hololens1眼镜开发盲人导航软件，第一次开发AR，和同学一起踩了不少坑，在此记录一下。

# 开发环境
> **结论：** 推荐使用Unity2017.4.40，对应Visual Studio2017版本
>
&emsp;&emsp;hololens1开发使用Unity和Visual Studio。 hololens1是微软2016年推出的老古董了，而且2019年就推出了arm64的hololens2（hololens1是x86架构），所以Unity比较新的版本基本上只适合hololens2的开发。
&emsp;&emsp;我们在Unity2021、2022、2023的版本都尝试过，但是远程调试的配置部分已经和官方文档所说的配置方法截然不同，我尝试了很久最终还是没有成功。另外，微软官方提供的案例教学使用的版本是Unity2017.2，我们测试了2017.4.40的版本，目前还没有出现什么问题。
&emsp;&emsp;Visual Studio要与Unity配合使用，安装2017版本即可。我是手动安装的，但在官网没有找到该版本的下载渠道，所以在网上随便找了个企业破解版的装了用。
&emsp;&emsp;Visual Studio需要安装以下组件：
- .net桌面开发；
- 通用windows平台开发（勾选"USB设备连接性"）
- 使用C++的桌面开发；
- 使用unity的游戏开发。
  
&emsp;&emsp;如果在Unity hub中和unity一起安装的VS，安装后可以检查一下是否缺少组件。
&emsp;&emsp;另外，关于virtual reality sdk，如果你看到过有关openXR的教程，那可以直接丢一边了，Hololens1使用Windows Mixed Reality API，不支持openXR（hololens2可以）。这个sdk后面配置unity项目的时候会看到。

# 相关学习文档
> 我们Hololens也有自己的games101：[Hololens101](https://learn.microsoft.com/zh-cn/windows/mixed-reality/develop/unity/tutorials/holograms-101) 


&emsp;&emsp;Hololens1从配置、调试、部署，到所有官方接口的学习，看过一遍100~240（其他的部分没太多干货），基本上就足够开发了。
&emsp;&emsp;事实上是，也找不到其他更多的学习资料了（大概不是因为我不够高性能）。不过对于这套文档，我愿称之Hololens1唯一指定学习教材，真保姆级教学，凛凛花来了都能看懂的那种(。
&emsp;&emsp;需要注意，它提供的视频教程是落后于文档教程的，有些旧代码和操作没有更新到最新（指7年前），建议首先根据文字教程操作，看不懂再去视频找找相关操作，大体上还是差不多的。
&emsp;&emsp;推荐大家把每一节github项目下下来，里面有Starter和Completed两份Unity项目，前者是我们可以拿来练习的，后者是已经做好的，可以拿来对比参考。

> 后日记：新看到Jitwxs的[博客](https://jitwxs.cn/categories/HoloLens/) ,这份开发笔记也很不错，可以作为补充资料或入门文档来学习

# 其他注意事项
- 配置项目时要先在`file-build setting`中切换UWP（通用windows平台），否则远程调试可能出问题；
- 应用部署到hololens时需要保持其常亮，否则网络连接不畅会部署失败；
- unity中脚本打开的VS版本选择方式：edit-preferences-external tools；
- 远程调试麦克风功能似乎不能正常使用，部署之后可以，调试的时候可以自己设置快捷键测试；
- 211课程手部引导功能远程调试有问题，部署之后是正常的；
- 212课程中SRGS测试没有成功，不确定是什么原因。

# 写在最后

&emsp;&emsp;内容差不多就是这些，第一次写这种记录，如果能帮到谁那就太好了。感觉写的不是很清晰，irtoa需要学习一下别人怎么写的，所以逛个知乎先~

// hololens1真的远古，想必也不会有人拿它来做开发吧= =

<center>
<img src="https://lqo-l.github.io/img/article/24.4.13/marisa.jpg" alt="一张动图"  width="1079" />
</center>