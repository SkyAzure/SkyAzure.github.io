---
title: 'Hexo generate报错TypeError: Cannot read property &#39utcOffset&#39 of null'
date: 2019-06-22 20:17:05
categories: 
- hexo
tags: 
- 踩坑
---

# 问题

最近刚刚开始使用Hexo，新建了一篇文章，运行`hexo g`时报错
<!-- more -->

```bash
TypeError: Cannot read property 'utcOffset' of null
```

# 原因

研究一番后发现是因为最初设置_config.yml中的时区时，我把`timezone: Asia/Shanghai`修改为`timezone: Asia/Beijing`

# 解决

在_config.yml中设置`timezone: Asia/Shanghai`

## 拓展

常用的程序语言支持的时区属于中国的有六个 …

- Asia/Chongqing
- Asia/Shanghai
- Asia/Urumqi
- Asia/Macao
- Asia/Hong_Kong
- Asia/Taipei

1949年以前，中国一共分了5个时区，以哈尔滨、上海、重庆、乌鲁木齐和喀什为代表，分别是：

* 长白时区GMT+8:30
* 中原标准时区GMT+8
* 陇蜀时区GMT+7
* 新藏时区GMT+6
* 昆仑时区GMT+5:30。 

它是1912年北京观象台制订，后由内政部批准过.北京也是GMT+8。可能是为了兼容旧的标准，没有新增`Asia/Beijing`