---
title: 'hexo删除&#34Hello Word&#34初始文章'
date: 2019-06-20 00:47:14
categories: hexo
tags: 
	- blog
	- skill 
---

# 起因

Hexo初始有一篇"Hello World"文章，我准备先删除掉它来开始我的blog生涯。但是一波操作之后，[刷新界面](skyazure.top)它还是在那个地方看着，于是学习了一下就有了这篇文章

# 步骤

一般文章的删除步骤为：

- 删除本地文件  

  `location:本地博客目录位置/source/_posts/你的文章`

- 生成

- 部署
<!-- more -->

```bash
hexo g
hexo d
```

但是我试过一次发现本地删掉了，`hexo g`报错，博客上还是存在这篇文章的。网上查阅后发现原因是_post文件夹不能为空，新建一篇就好了

# 解决办法

`hexo n "博客名字"`

**保证_post文件夹不为空就好了**

## 拓展

在使用hexo写文章时，如果文章的title中包含双引号”abc”、&#36;符号时会编译出错，文章无法渲染。
由于这里的写法是yml语法，”、$这些都是特殊符号，执行hexo -s时到编译title这里就会出现错误

解决办法

这里我们需要对特殊符号进行转义，用对应的HTML字符实体进行替换

附录：各种常用特殊字符对应的HTML字符实体

```html
! &#33; — 惊叹号 Exclamation mark
" &#34; &quot; — 双引号 Quotation mark
# &#35; — 数字标志 Number sign
$ &#36; — 美元标志 Dollar sign
% &#37; — 百分号 Percent sign
& &#38; &amp; — 与符号(&) Ampersand
' &#39; — 单引号 Apostrophe
( &#40; — 小括号左边部分 Left parenthesis
) &#41; — 小括号右边部分 Right parenthesis
* &#42; — 星号 Asterisk
+ &#43; — 加号 Plus sign
< &#60; &lt; 小于号 Less than
= &#61; — 等于符号 Equals sign
- &#45; &minus; — 减号
> &#62; &gt; — 大于号 Greater than
? &#63; — 问号 Question mark
@ &#64; — Commercial at
[ &#91; — 中括号左边部分 Left square bracket
\ &#92; — 反斜杠 Reverse solidus (backslash)
] &#93; — 中括号右边部分 Right square bracket
{ &#123; — 大括号左边部分 Left curly brace
| &#124; — 竖线Vertical bar
} &#125; — 大括号右边部分 Right curly brace
空格 &nbsp;
```











