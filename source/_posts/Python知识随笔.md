---
title: Python知识随笔
date: 2019-10-11 10:44:12
categories:
- Python
tags:
- Python
---

# python知识随笔

## 正则表达式的贪婪与非贪婪匹配

`String str="abcaxc"; `

`Patter p="ab*c";`

- 贪婪匹配：正则表达式一般趋向于最大长度匹配，也就是所谓的贪婪匹配。如上面使用模式p匹配字符串str，结果就是匹配到：abcaxc(ab*c)。

- 非贪婪匹配：就是匹配到结果就好，就少的匹配字符。如上面使用模式p匹配字符串str，结果就是匹配到：abc(ab*c)。