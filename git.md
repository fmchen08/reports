# 使用Git
[TOC]
## 1. Git简介
### 1.1 安装Git
下载地址：https://git-scm.com/download

安装后，搜索栏中输入cmd打开命令行终端或运行Git Bash，输入命令：

    git --version

查看是否安装成功。

### 1.2 设置用户名和邮箱
在终端中，输入如下命令：

    git config --global user.name "Your Name"
    git config --global user.email "your@email.com"

双引号中内容替换成你的用户名和邮箱地址。不是用来登录，只是用来跟踪记录谁对代码做了什么修改。

* 注意：Git和Github是不同的两个东西，Github依赖于Git，但Git也可以单独使用。

## 2. 仓库（Repositories）
在Git中，仓库是项目的容器。有两种容器：

*  本地仓库 - 只存储于你自己的计算机
*  远程仓库 - 存储于远程服务器。在团队合作时很有用。你可以分享自己的代码，看别人的代码并融合到本地项目中，也可以修改远程仓库中的代码。
  
这个说明文档只针对本地仓库。

## 3. 创建仓库
使用Git管理项目，即使是只有一个文件的项目，也需要创建一个仓库。打开终端，进入到项目的主文件夹，输入下面的命令：

    git init

![l7i3ZV.png](https://s2.ax1x.com/2020/01/13/l7i3ZV.png)

## 4. 提交代码
使用Git，你可以无数次修改和提交代码，所有的提交历史都有记录，可以回退到任何一个提交过的程序版本。

- 什么时候提交？在项目开发过程中，添加新内容、修改函数功能、或修复bug等。

### 4.1 检查状态
在项目路径下，用下面的命令检查仓库的状态：

    git status

![l7FrXn.png](https://s2.ax1x.com/2020/01/13/l7FrXn.png)

