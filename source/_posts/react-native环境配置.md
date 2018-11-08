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
 <!-- more -->

3. 配置Java的环境变量

   * 添加环境变量JAVA_HOME = C:\Program Files\Java\jdk1.8.0_45;

   *  Path+=%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;

   * CLASSPATH+=%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;


JAVA_HOME变量：

![JAVA_HOME](http://images2015.cnblogs.com/blog/546421/201607/546421-20160709102408874-1736443714.png)

​	

CLASSPATH变量

![CLASSPATH变量](http://images2015.cnblogs.com/blog/546421/201607/546421-20160709102528280-1866646025.png)

二、安装 android SDK

1. 下载 android sdk 并安装；

2. 安装完成后根据 react-native官网 安装 SDK Tools;

3. 配置android环境变量

 * 添加 ANDROID_HOME 变量
 ![android-home](http://images2015.cnblogs.com/blog/546421/201607/546421-20160709103101952-2112122131.png)

* 在 Path 变量里添加 %ANDROID_HOME%\tools;%ANDROID_HOME%\platform-tools;

三、安装node.js git 环境

四、安装react-native 的命令行工具 react-native-cli

```
npm install react-native-cli -g
```

***备注：*** 官网讲需要安装 python 环境，但是个人感觉好像没用，一直也没安装过，所以安不安装看个人；


### 创建我们的项目

1. 生成项目
```
react-native init myApp
```


2. 安装项目依赖包
```
npm install
```

3. 连接真机或者模拟机，在终端运行 adb devices 查看是否连接设备，真机需要打开开发者模式，然后运行 react-native run-android 生成 apk 安装包。


4. 运行 package.json ，命令行运行

```
react-native start 或者  npm start
```


5. 打开手机上我们安装的app，会出现如下所示的情况 :

![error](http://images2015.cnblogs.com/blog/546421/201607/546421-20160709113415499-1546806111.png)


这时候摇一摇手机，点击Dev Settings后，点击Debug server host & port for device,设置IP和端口

![reload](http://images2015.cnblogs.com/blog/546421/201607/546421-20160709114104467-1570314774.jpg)

再次摇一摇手机，选择Reload ，程序就运行起来，出现Welcome to React Native！

![sucess](http://images2015.cnblogs.com/blog/546421/201607/546421-20160709114253046-223755573.png)

现在就可以尽情的写我们的 code 了。。。

