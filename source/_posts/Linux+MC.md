---
layout: post
title: Play Minecraft on Ubuntu 
date: 2015-2-11
description: "Minecraft"
tags: [Linux,Minecraft]
---

# 在Ubuntu上玩Linux

## 前言

windows上的MC玩起来方便，不管是服务器端还是客户端，都有很多大神打造的启动器，开服器，可在Linux上，这些工具就少了些，并且经常会出错。网上的很多资料大多是针对经典的旧版，我会介绍一种简单的方法在Ubuntu Linux上玩起MC1.8。

## 工具
1. MinecraftSP.jar
2. Hello Minecraft Launcher 2.2.1
3. Minecraft 1.8 纯净客户端
4. OpenJDK 7

<!-- more -->

## Java环境搭建
可以在Ubuntu自带的软件中心中安装OpenJDK 7 runtime，也可以用apt-get的方式来安装

```bash
sudo apt-get install openjdk-7-jdk
```

在安装完成后输入：

```bash
java -version # 查看版本号
```

如果显示出了 Java 版本号那就已经安装成功。

## 安装游戏

右击MinecraftSP.jar

点`属性`-`权限`，在`执行`后面的`允许作为程序执行文件`前打勾选上。

然后双击，输入帐号密码，点`Login`开始加载Classic版也就是1.5.4的MC。
这个是必须的，为后面玩上1.8做前提，因为自1.6.2以后就不提供bin文件包，很多在Ubuntu运行失败的都是因为缺少bin。

待下载完成后就可以玩经典版的了，可以设置为中文。

## 安装MC 1.8
必须先运行一次经典版的MC，让其产生一些必要的文件，然后才能继续安装MC 1.8
然后将纯净包里的东西覆盖到本机的`.Minecraft`中。

## HMCL的使用
在终端里输入

```bash
sh HMCL-2.2.1.sh #记得先cd进入HMCL的文件夹
```

然后就会出现启动器，在游戏设置里可以安装些资源或游戏下载

然后就可以玩了

注意，这时候虽然安装了1.8，但用MinecraftSP来启动仍然是经典版本，想要玩1.8版本必须用启动器

## 一些错误

* 首次启动后黑屏
	
	* bin文件包里的java库文件没有生效，可以去网上下lwjgl-2.9.0文件，然后分别替换原文件
	* 可能是内存分配太少，建议512MB
	* 显卡驱动缺少也有可能
	* Mod不兼容

* 缺少Java库，缺少lwjgl.jar等等
例如

```html
*** Hello Minecraft! Launcher 2.1.9 ***
*** Invoking minecraft main() ***
ERROR StatusLogger Unable to locate a logging implementation, using SimpleLogger
Minecraft崩溃了！
可能是游戏依赖库不完整或解压依赖库时出错。可以通过下载整合包解决问题。
java.lang.reflect.InvocationTargetException
at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
at java.lang.reflect.Method.invoke(Method.java:606)
at org.jackhuang.hellominecraft.launcher.Launcher.main(SourceFile:122)
Caused by: java.lang.UnsatisfiedLinkError: no lwjgl in java.library.path
at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1886)
at java.lang.Runtime.loadLibrary0(Runtime.java:849)
at java.lang.System.loadLibrary(System.java:1088)
at org.lwjgl.Sys$1.run(Sys.java:73)
at java.security.AccessController.doPrivileged(Native Method)
at org.lwjgl.Sys.doLoadLibrary(Sys.java:66)
at org.lwjgl.Sys.loadLibrary(Sys.java:95)
at org.lwjgl.Sys.<clinit>(Sys.java:112)
at bss.I(SourceFile:2488)
at net.minecraft.client.main.Main.main(SourceFile:41)
... 5 more


*** Main class main() finished ***

```

这些问题大部分都是因为bin文件出了问题，或者没装bin文件
我一开始用纯净包+启动器，发现各种运行不起来
后来排查，还是缺少bin文件，介于网上完整的ubuntu包很少，所以只能用MinecraftSP来进行安装。

#### 暂时只知道的ubuntu上自己看到的一些错误

在Ubuntu服务器端搭建Minecraft server 按照网上的步骤都可以成功搭建的。
