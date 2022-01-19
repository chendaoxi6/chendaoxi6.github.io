---
categories:
  - Computer Science
tags:
  - Tool
  - C/C++
---

[cnblogs链接]([https://www.cnblogs.com/linkchen/p/13657939.html](https://www.cnblogs.com/linkchen/p/13657939.html))

## Cygwin

官网：[cygwin](http://www.cygwin.com/)

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181629954-1041088465.png" alt="1">

下载64bit安装器，并打开选择next

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181652633-619817042.png" alt="2">

尽量不要装在系统盘

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181656975-537319462.png" alt="3">

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181702409-1881822572.png" alt="4">

我们选择使用国内的镜像完成，官网提供的各国镜像信息：`https://cygwin.com/mirrors.html`

我们选择使用USTC中科大的Mirror，网址：`http://mirrors.ustc.edu.cn/cygwin/`

一路next，到这里我们选择第三项使用代理，并将镜像地址添加进去

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181754903-210025715.png" alt="5">

在这里next会提示错误，我们选择ok

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181801309-1040747942.png" alt="6">

我们将镜像地址填入URL栏中，选择Add

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181804863-1017590552.png" alt="7">

注意然后需要选择back，并选择Direct Connection直接连接，选择next

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181810710-1753179206.png" alt="8">

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181814269-1331746691.png" alt="9">

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181818480-1636882183.png" alt="10">

加载完成后，会显示各种包，我们在search中输入gcc，并展开All，找到Devel、Libs目录下的

* gcc-core

* gcc-g++ 【需要C++的可以装】

* libgccpp1【需要C++的可以装】

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181825726-595518704.png" alt="11">

同理搜索安装Devel下的gdb

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181828822-1879888883.png" alt="12">

最后安装Devel下的make、cmake

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181831722-1599751522.png" alt="13">

选择next进行安装

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181845103-254832431.png" alt="14">

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181848189-2080452507.png" alt="15">

安装完成

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181857531-1243416934.png" alt="16">

## GCC Environment Variables

和配置一般Path环境变量一样，找到cygwin安装目录下的bin目录，比如我这里：E:\cygwin64\bin

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181917454-341522598.png" alt="17">


配置完成后，打开cmd，输入gcc -v，检查是否存在错误

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181922595-2031351806.png" alt="18">


同理输入g++ -v查看g++版本

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181926448-424152631.png" alt="19">


## CLion

[Jetbrains官网](https://www.jetbrains.com/clion/)

常规安装方法，不建议装系统盘，一路next就行

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181930951-2047180142.png" alt="20">

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181934790-1068245940.png" alt="21">

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181938794-657979178.png" alt="22">

安装结束后，打开CLion，激活方法我这里选择的是教育认证，如果是学生大家可以自己到jetbrains官网上去看看怎么操作

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912181958204-592071862.png" alt="23">

激活完成后，CLion会自动检测gcc环境

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912182002347-1065959994.png" alt="24">

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200912182007186-914286403.png" alt="25">

然后就可以开始在Win10系统上使用gcc进行简单开发，本文如有不正确的地方欢迎指正
