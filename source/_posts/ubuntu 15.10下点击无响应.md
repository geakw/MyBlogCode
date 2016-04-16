---
title: Ubuntu 15.10下vpn点击无响应
date: 2016-04-16 16:27:21
categories: system
---

最近需要在ubuntu系统下科学上网，之前用的mac和windows下的vpn连接都是挺正常的，可以在ubuntu 15.10下面按照网上的教程来，点击vpn连接完全没有任何反应，尝试了很多次，卸载系统默认的networkmanager，自己编译安装也不行，strongswan也换过了，但就是么有任何反应，这个倒霉的问题看来遇到的人很少，话说ubuntu现在连基本功能都做不好，之所以这么说是因为我装了个14.04的LTS版也是这样的，但是最终只要功夫深，铁杵磨成针，经过无数次尝试，终于找到个方法解决了这个问题，如果你也碰到这个现象，不妨尝试下面的操作：

sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start
sudo gedit /etc/NetworkManager/NetworkManager.conf //打开文件后，将最下面把false改成true
sudo service network-manager restart

按照上面命令的敲一遍之后，再连接vpn，成功弹出vpn连接成功的通知
