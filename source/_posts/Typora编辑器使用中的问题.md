---
title: hexo不解析Markdown标题&#40&#35&#41
date: 2019-06-22 21:07:03
categories: Markdown
tags: 
- Markdown编辑器
- 踩坑
---

# 问题

发布文章后标题没有被解析显示`#标题` ，但是在我编辑器(Typora)里面显示没有问题
<!-- more -->

# 原因

Markdown标题标准写法需要在"#"和后面字符之间加一个空格

不加空格一些引擎就解析不了

Typora编辑器中在行首有#，就会自动识别为标题

# 注意

需要注意写Markdown文档时要严格遵守Markdowm标准

## 拓展

**Markdown**诞生自 [Daring Fireball](https://link.zhihu.com/?target=http%3A//daringfireball.net/)之手，点击[这里](https://link.zhihu.com/?target=http%3A//daringfireball.net/projects/markdown/syntax)可以找到最早版本的语法标准。然而，它的语法标准因解析器和编辑器而异，**Typora**使用的是[GitHub Flavored Markdown](https://link.zhihu.com/?target=https%3A//help.github.com/articles/github-flavored-markdown/)标准。

需要注意的是在Markdown中的HTML代码块可以被识别但并不会被解析和编译。同样要注意的是，保存之后的文档格式可能会对最初的编写的文档格式有所微调。



