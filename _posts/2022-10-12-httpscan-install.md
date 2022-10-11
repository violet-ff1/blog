---
layout: post
title: Httpscan工具使用
subtitle: 避坑
gh-repo: violet-ff1/blog
gh-badge: [star, fork, follow]
tags: [原生JDBC]
comments: true
---

碌碌虚无

**Httpscan是一个扫描指定网段的Web主机的小工具。和端口扫描器不一样，Httpscan是以爬虫的方式进行Web主机发现，因此相对来说不容易被防火墙拦截。**

先检查python环境是否为2.x版本（Httpscan中的python语法版本为2.x）

1.下载Httpscan 地址：https://github.com/zer0h/httpscan

2.配置环境变量
a.python2.x\根目录
b.python2.x\Scripts

3.下载 wget.exe 地址：https://eternallybored.org/misc/wget/

4.wget https://bootstrap.pypa.io/pip/2.7/get-pip.py
python get-pip.py
这里是为了解决pip版本问题

5.pip install requests （Requests 库是在 urllib 的基础上开发而来，它使用 Python 语言编写，并且采用了 Apache2 Licensed（一种开源协议）的 HTTP 库。与 urllib 相比，Requests 更加方便、快捷，因此在编写爬虫程序时 Requests 库使用较多）

6.pip install IPy （IPy 模块包含IP类，可以方便的处理绝大部分个是为IPv6和IPv4的网络和地址。可以通过version方法就可以分出IPv4和IPv6）

7.httpscan根目>python httpscan.py IP

8.大功告成
