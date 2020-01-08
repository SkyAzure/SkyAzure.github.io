---
title: Linux知识随笔
date: 2019-10-11 10:44:34
categories:
- Linux
tags:
- 随笔
---

# Linux知识随笔

## 1.Linux内核五大模块

- 进程调度模块

- 内存管理模块

- 文件系统模块

- 进程间通信模块

- 网络接口模块

  <!-- more -->

## 2.死锁

### 要点提示

1. 掌握死锁的概念和产生死锁的根本原因。

2.  理解产生死锁的必要条件--以下四个条件同时具备：互斥条件、不可抢占条件、占有且申请条件、循环等待条件。

3.  记住解决死锁的一般方法，掌握死锁的预防和死锁的避免二者的基本思想。

4.  掌握死锁的预防策略中资源有序分配策略。

5.  理解进程安全序列的概念，理解死锁与安全序列的关系。

6.  了解银行家算法。

7.  了解资源分配图。

8.  了解死锁的检测及恢复的思想。

   ————————————————

   > 原文链接：https://blog.csdn.net/abigale1011/article/details/6450845

死锁产生的原因：
（1）竞争资源
（2）进程推进顺序不当

## 3.TCP/IP协议详解

> [参考文章](https://zhuanlan.zhihu.com/p/33889997)

## 4.最受欢迎的Linux发行版(现第2), Manjaro折腾全记录（超长超详细）

> [参考文章](https://cloud.tencent.com/developer/article/1390999)

## 5. 对于一个分布式计算系统来说3个指标不能同时完成

- 一致性

- 可用性
- 分区容错性

## 6.OSI参考模型中各层作用

<img src="/Users/sky/Desktop/OSI七层模型详解.gif" alt="OSI七层模型详解" style="zoom:50%;" />

物理层：通过媒介传输比特,确定机械及电气规范（比特Bit）
数据链路层：将比特组装成帧和点到点的传递（帧Frame）
网络层：负责数据包从源到宿的传递和网际互连（包PackeT）
传输层：提供端到端的可靠报文传递和错误恢复（段Segment）
会话层：建立、管理和终止会话（会话协议数据单元SPDU）
表示层：对数据进行翻译、加密和压缩（表示协议数据单元PPDU）
应用层：允许访问OSI环境的手段（应用协议数据单元APDU）



网络层：

- IP协议
- ICMP协议
- ARP协议
- RARP协议。 

传输层：

- UDP协议
- TCP协议。

应用层：

- FTP（文件传送协议）
- Telenet（远程登录协议）
- DNS（域名解析协议）
- SMTP（邮件传送协议）
- POP3协议（邮局协议）
- HTTP协议
- SNMP协议
- TFTP

## 7.OSI七层模型和TCP/IP四层模型

### OSI七层模型各层协议：

1. 物理层：RJ45、CLOCK、IEEE802.3

2. 数据链路层：PPP、FR、HDLC、VLAN、MAC

3. 网络层：IP、IPX、OSPF、RIP、IGRP、ICMP、ARP、RARP

4. 传输层：TCP、UDP、SPX

5. 会话层：NFS、SQL、NETBIOS、RPC

6. 表示层：JPEG、MPEG、ASII

7. 应用层：Telnet、HTTP、FTP、WWW、NFS、SMTP

### TCP/IP四层模型：

#### 一、TCP/IP四层模型名称：

网络接口层（Network Access）【又分为物理层（Physical）和数据链路层（Datalink）】→网络互联层（Internet）→传输层（Transport）→应用层（Application）

#### 二、TCP/IP四层模型各层的功能：

1.  网络接口层：负责实际数据的传输

2. 网络互联层：负责网络间的寻址数据传输

3. 传输层：负责提供可靠的传输服务

4. 应用层：负责实现一切与应用程序相关的功能

#### 三、TCP/IP四层模型各层的协议：

1、网络接口层：HDLC（高级链路控制协议）、PPP（点对点协议）、SLIP（串行线路接口协议）

2、网络互联层：IP（网际协议）、ICMP（网际控制消息协议）、ARP（地址解析协议）、RARP（反向地址解析协议）

3、传输层：TCP（控制传输协议）、UDP（用户数据报协议）

4、应用层：FTP（文件传输协议）、HTTP（超文本传输协议）、DNS（域名服务器协议）、SMTP（简单邮件传输协议）、NFS（网络文件系统协议）

#### 四、OSI七层模型和TCP/IP四层模型的区别：

OSI七层模型和TCP/IP四层模型最大的区别在于：OSI七层模型是一个理论上的网络通信模型，而TCP/IP四层模型则是实际运行的网络协议。
