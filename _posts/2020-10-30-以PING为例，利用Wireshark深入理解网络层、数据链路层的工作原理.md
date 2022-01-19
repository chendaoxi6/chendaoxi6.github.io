---
categories:
  - Computer Science
tags:
  - Network
  - Tool
---

[cnblogs链接](https://www.cnblogs.com/linkchen/p/13900405.html)

## Wireshark

Wireshark（前称Ethereal）是一个网络封包分析软件。网络封包分析软件的功能是撷取网络封包，并尽可能显示出最为详细的网络封包资料。Wireshark使用WinPCAP作为接口，直接与网卡进行数据报文交换

官网：https://www.wireshark.org/

下载并安装完成后，打开显示如下界面

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202010/1560524-20201030091051067-1237007771.png" alt="1">

## IP datagram IP数据报

图解：

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202010/1560524-20201030091115514-1606767107.png" alt="2">

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202010/1560524-20201030091120304-1247361889.png" alt="3">

## Ethernet V2 frame 以太网V2的MAC帧格式

| Preamble | Start of frame delimiter | MAC destination | MAC source | Ethertype |    Payload     | Frame check sequence (32‑bit CRC) |
| :------: | :----------------------: | :-------------: | :--------: | :-------: | :------------: | :-------------------------------: | :--: | :--: | ---- |
| 7 octets |         1 octet          |    6 octets     |  6 octets  | 2 octets  | 46‑1500 octets |             4 octets              |

中文对照解释

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202010/1560524-20201030091128672-655840210.png" alt="4">

注意：Wireshark抓不到以太网V2的MAC帧格式中，帧尾4字节的FCS校验序列，以及帧首8字节的前同步码+帧开始定界符

## PING

Ping是工作在 TCP/IP网络体系结构中应用层的一个服务命令， 主要是向特定的目的主机发送ICMP（Internet Control Message Protocol 因特网报文控制协议）Echo 请求报文，测试目的站是否可达及了解其有关状态

ping的用法

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202010/1560524-20201030091137087-1708189094.png" alt="5">

## Wireshark抓包结果与分析

打开Wireshark，选择需要抓取的网络，选择开始捕获Start capture

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202010/1560524-20201030091143673-230217708.png" alt="6">

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202010/1560524-20201030091152356-1366937553.png" alt="7">

现在局域网中有两台电脑，分别是本机和一台手机，在本机打开cmd

输入```ipconfig /all```，本机IP地址和网卡的MAC地址

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202010/1560524-20201030091202426-1147682875.png" alt="8">

得到本机的IP地址：192.168.110.246，MAC地址：F8-63-3F-90-A1-1E

打开手机，查看手机的IP地址和MAC地址

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202010/1560524-20201030091216541-892374922.png" alt="9">
得到手机的IP地址：192.168.108.95，MAC地址：C2-F7-3D-3E-CB-67

输入```ping 192.168.108.95 -t```，-t的意思是直到手动停止之前一直ping下去

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202010/1560524-20201030091222020-368754515.png" alt="10">

在Wireshark中找到捕获的对应ip的包

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202010/1560524-20201030091229035-415114217.png" alt="11">

双击其中的一条request请求，可以看到整个Packet格式如下

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202010/1560524-20201030091236489-2110084536.png" alt="12">

下面我们来分析这段数据，对应之前所说的以太网V2的MAC帧格式和IP数据报

```
c2 f7 3d 3e cb 67 f8 63 3f 90 a1 1e 08 00 45 00
00 3c a3 7d 00 00 80 01 3a 9d c0 a8 6e f6 c0 a8
6c 5f 08 00 44 bf 00 01 08 9c 61 62 63 64 65 66
67 68 69 6a 6b 6c 6d 6e 6f 70 71 72 73 74 75 76
77 61 62 63 64 65 66 67 68 69
```

Wireshark抓不到以太网V2的MAC帧格式中，帧尾4字节的FCS校验序列，以及帧首8字节的前同步码+帧开始定界符

首先分析MAC帧

* 开始的6个字节C2-F7-3D-3E-CB-67，是目的地址，即手机
* 随后的6个字节F8-63-3F-90-A1-1E，是源地址，即本机
* 随后的2个字节08 00H，是类型，IPv4对应的值即0x0800

接着分析IP数据报的首部，固定部分共20字节

* 第1个字节为45H，前4位表示版本二进制0100，即IP Version4，后4位表示首部长度0101即十进制5，而IP数据报以4个字节为单位，4*5=20，即首部为20字节
* 第2个字节为区分服务，00H
* 第3、4个字节为总长度，00 3cH，即60个字节

* 第5、6个字节为标识，a3 7dH
* 第7、8个字节的前3位为标志位，后13位为片偏移，00 00H
* 第9个字节表示生存时间TTL，80H，单位为跳数，即128跳，TTL的最大值为2^8-1=255
* 第10个字节为协议，01H表示ICMP协议，具体对照表可见wikipedia，https://en.wikipedia.org/wiki/List_of_IP_protocol_numbers
* 第11、12个字节为首部校验和，3a 9dH
* 第13、14、15、16个字节为源地址，c0 a8 6e f6H，对应的十进制数为192.168.110.246，即本机IP地址
* 第17、18、19、20个字节为目的地址，c0 a8 6c 5f，对应的十进制数位192.168.108.95，即手机的IP地址

剩下的所有字节都是数据部分，以ICMP协议的格式呈现

通过展开Wireshark解析的每一项可以很清晰地看出Packet的组成

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202010/1560524-20201030091247422-935675101.png" alt="13">

使用Wireshark可以帮助我们更深入地理解网络层、数据链路层的工作原理
