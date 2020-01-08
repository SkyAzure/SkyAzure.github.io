---
title: Git安装及Github基本使用
date: 2019-06-27 15:32:58
categories:
- Git
tags:
- GitHub
---

# 目录

- 安装git
- 创建ssh key 、配置git
- 提交本地项目到Github
<!-- more -->

## 安装git

在Mac上安装git

首先在终端输入`git`查看是否已安装过git

### 通过homebrew安装git

- 未安装homebrew，先安装homebrew

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

- 安装git

```bash
brew install git
```

## 创建ssh key、配置git

1. 设置username和email（github每次commit都会记录他们）

```bash
git config --global user.name "你的用户名"
git config --global user.email "你的邮箱地址"
```

2. 生成ssh key

```bash
ssh-keygen -t rsa -C "你的邮箱地址"
```

然后直接三个回车即可，默认不需要设置密码

然后找到~/下生成的.ssh的文件夹中的id_rsa.pub密钥，将内容全部复制

3. 打开[GitHub_Settings_keys](https://link.zhihu.com/?target=https%3A//github.com/settings/keys)页面，新建new SSH Key

![屏幕快照 2019-06-28 下午9.02.22](/Users/sky/Desktop/屏幕快照 2019-06-28 下午9.02.22.png)

Title为标题，任意填即可，将刚刚复制的id_rsa.pub内容粘贴进去，最后点击Add SSH key。
在Git Bash中检测GitHub公钥设置是否成功，终端输入 `ssh git@github.com` 

```bash
Last login: Sat Jan  6 14:42:55 on ttys000
你的主机名:~ 你的用户名$ ssh git@github.com 
Hi 你刚刚设置的user.name! You've successfully authenticated, but GitHub does not provide shell access.
```

说明已经链接成功。

## 提交本地项目到Github

1. 在GitHub上新创建一个 repository或者**Start a Project**
2. 填写项目信息，填写完成后点击**Create repository**
3. Clone工程到本地，首先复制ssh 地址

 然后克隆项目,终端输入

```bash
git clone 你复制的ssh地址
```

这时，工程已经被克隆到所在文件夹

4. 进入clone下来的文件夹，使用编辑器等修改并保存代码
5. 提交修改，首先切换到文件夹所在目录

```bash
cd clone下来的文件夹的地址
//文件添加到仓库（.代表提交所有文件）
git add .
//把文件提交到仓库
git commit -m "First Commit"
//上传到github
git push
```

查看GitHub上的项目，就已经上传成功啦

#### 参考文章

1. [Git教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
2. [GitHub+Hexo 搭建个人网站详细教程](https://zhuanlan.zhihu.com/p/26625249)