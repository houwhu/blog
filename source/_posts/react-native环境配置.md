---
title: react-native环境配置
date: 2018-11-07 22:41:17
type: 'tags'
tags:                 
- react-native
categories:
- react-native
---

### react-native window开发环境搭建

一、安装JDK

1. 从 [Java官网](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) 下载JDK并安装。

2. 安装成功可以用java -version查看版本信息，或用 java -c 检测是否安装成功

3. 配置Java的环境变量

   * 添加环境变量JAVA_HOME = C:\Program Files\Java\jdk1.8.0_45;

   *  Path+=%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;

   * CLASSPATH+=%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;

      <!-- more -->

JAVA_HOME变量：

![JAVA_HOME](http://images2015.cnblogs.com/blog/546421/201607/546421-20160709102408874-1736443714.png)

​	

CLASSPATH变量

![CLASSPATH变量](http://images2015.cnblogs.com/blog/546421/201607/546421-20160709102528280-1866646025.png)

