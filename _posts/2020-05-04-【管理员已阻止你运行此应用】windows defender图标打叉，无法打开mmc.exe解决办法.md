---
categories:
  - Others
tags:
  - Tool
---

今天开机遇到一个奇怪的问题，发现windows defender图标上面打了个×：

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202005/1560524-20200504171615189-445842819.jpg" alt="1">

打开按照系统提示需要restart服务，但是无法重启服务，会出现错误，然后尝试手动重启服务，准备打开管理控制台mmc，但是打开出现如图错误：

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202005/1560524-20200504171654766-408079869.jpg" alt="2">

寻找解决办法，打开防火墙允许mmc.exe通过防火墙：

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202005/1560524-20200504171841594-2009679775.jpg" alt="3">

按图1、2、3、4，将c:\windows\system32\mmc.exe添加到允许列表中：

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202005/1560524-20200504171855387-727345647.jpg" alt="4">

勾上专用和公用：

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202005/1560524-20200504171902261-563112187.jpg" alt="5">

重启电脑，一定要重启电脑：

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202005/1560524-20200504172134012-1384716243.png" alt="6">

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202005/1560524-20200504172211942-1975379909.png" alt="7">

