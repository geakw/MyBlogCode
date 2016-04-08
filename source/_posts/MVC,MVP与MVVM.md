---
title: MVC、MVP与MVVM
date: 2016-04-08 18:42:39
categories: 架构
---
在客户端的开发中，有经验的开发人员经常使用一些MV*架构模式，来对应用进行分层处理，这样做的好处是分工明确，每个模块只做自己应该做的事情。由于自己在平时的开发中使用MVP模式比较多一些，最近看到自从Android支持Data binding之后，MVVM也很受追捧，在github上面可以看到很多Mvp转成MVVM的demo，比如:

[MVVM_Android-CleanArchitecture](https://github.com/zhengxiaopeng/MVVM_Android-CleanArchitecture)
 
[mvp-to-mvvm-transition](https://github.com/Nilzor/mvp-to-mvvm-transition)

刚好有时间，就研究了一下MVC,MVP,MVVM的区别，现在做一下总结

<!--more-->

1、MVC

![](http://i.imgur.com/ciKCnrd.png)

MVC是把应用分成了Model，View，Controller三层。当用户与view进行交互时，会由Controller进行逻辑的处理，并更改Model。MVC与MVP的重要区别是Controller并不会直接操作View，View和Model的同步是通过观察者模式进行的，当Model改变后会发出相应的事件，通知View进行重新获取Model更新。

2、MVP

![](http://i.imgur.com/dcCuZbn.png)

MVP把MVC中的Controller换成了Presenter，当用户与view交互时，由Presenter进行逻辑的处理，并对Model进行更改，与MVC不同的时，MVP由Presenter负责View的更新，View并不清楚Model的存在，Presenter是连接View和Model的桥梁。

3、MVVM

![](http://i.imgur.com/qPDSr9H.png)

MVVM代表的是Model-View-ViewModel，之所以叫做ViewModel是因为它是The Model of View的意思，是View的一个模型，ViewModel是用来连接View和Model的桥梁，ViewModel中有一个Data binding engine，负责View和Model之间的同步，我们只需要根据语法，指令式地声明View上的显示的内容是和Model的哪一块数据绑定的，当用户操作View时，engine会自动把数据更新到Model中，反之，当Model改变时，engine也会自动把数据更新到View上，这称之为双向数据绑定（Two-way data-binding）

参考文档：

[android-databinding-goodbye-presenter-hello-viewmodel](http://tech.vg.no/2015/07/17/android-databinding-goodbye-presenter-hello-viewmodel/)

[Approaching Android with MVVM](https://labs.ribot.co.uk/approaching-android-with-mvvm-8ceec02d5442#.6ebkxxpsu)

[界面之下：还原真实的MV*模式](https://github.com/livoras/blog/issues/11)