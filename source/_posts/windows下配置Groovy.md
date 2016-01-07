---
title: windows下配置Groovy
date: 2016-01-07 14:19:09
categories: Scripts
---
windows下配置Groovy环境的教程网上很容易搜到，我参考的是[这篇文章](http://www.jianshu.com/p/777cc61a6202)，安装过程一切顺利，然而在cmd中运行Groovy -v命令时返回ERROR: JAVA_HOME is set to an invalid directory，第一反应是我的JAVA_HOME变量配置的有问题，但cmd中运行java -version正常，应该不是这个变量的问题。
![](http://i.imgur.com/Vp0QM99.jpg)

谷歌后发现这是Groovy的一个[issue](https://issues.apache.org/jira/browse/GROOVY-6023),这确实是有点坑，而且发现有这个问题还没有在最新的版本里面进行更改，so没办法，只能自己改了，废话不说，直接上步骤：

1、在Groovy根目录中进入bin文件夹，打开startGroovy bat文件  

2、将下面一行  

  ![](http://i.imgur.com/EleLUen.jpg)  
  修改为 if exist "%JAVA_HOME%\bin\java.exe" goto valid_JAVA_HOME_DIR  
  ![](http://i.imgur.com/McMpCKt.jpg)  
然后运行Groovy -v，返回结果正常O(∩_∩)O~  
  ![](http://i.imgur.com/1r8NUSD.jpg)