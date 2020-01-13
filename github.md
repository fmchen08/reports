# 使用Github
[TOC]
## 1. Github简介
Github是Git仓库的托管平台。你可以单独使用Git，但是难以与他人合作和分享代码。

* Git是版本控制系统，检查跟踪文件变化
* Github为Git项目提供托管服务

使用Github，我们可以将本地的项目仓库上传到基于云服务的远程Github仓库，也可以与其他开发者的公开仓库进行交互。Github可以看做开发者的社交网络，用户可以互相关注、打分、合作和交流。

开发者可以下载Github远程仓库的代码，使用或在本地继续开发，开发完成后，将修改推送到Github远程仓库。其他开发者或项目成员可以将项目下载到自己的计算机，从而保持项目开发的同步。

## 2. 开始使用Github
### 2.1 注册账户
首先，注册一个账户 https://github.com/

### 2.2 工作流程
将现有仓库推送到Github
  
* 将代码提交到本地仓库
* 登录Github，创建一个新仓库
* 将本地仓库关联到github仓库（添加一个远程仓库）
* 使用远程仓库将代码推送到github

![l7Uk5T.png](https://s2.ax1x.com/2020/01/13/l7Uk5T.png)

![l7UexJ.png](https://s2.ax1x.com/2020/01/13/l7UexJ.png)

查看远程仓库：

    git remote -v

将 github上的命令复制到终端：
第一步：创建远程仓库，ogrin是远程仓库的名字，也可以用其他名字。

    git remote add origin https://github.com/fmchen08/reports.git

然后，把master分支推送到origin

    git push -u origin master

![l7wZRS.png](https://s2.ax1x.com/2020/01/13/l7wZRS.png)

查看Github，可以看到项目更新。包括所有的提交记录。

### 2.3 合作
在Github中可以设置允许其他合作者编辑修改代码。

在该项目菜单行找到settings, 选择collaborators，通过名字或email搜索账户。被选中的人就可以修改和提交代码了。

输入命令拉取项目，能够看到项目的修改情况。

    git pull origin master

对于新的内容，可以创建一个新分支，把新分支推送到origin。

### 2.4 克隆项目
* 在本地新建一个文件夹，切换到该文件夹路径下。
* 复制github上某个项目的链接，比如DeepFake。这时会把该项目所有的代码和commits下载到本地。如果你没有合作者权限，是不可以修改并推送该项目的。
![l7Xlin.png](https://s2.ax1x.com/2020/01/13/l7Xlin.png) 

### 2.5 社区贡献
* 如果你想为开源项目作出贡献，需要申请。首先，在Github上fork该项目，这样在你自己的Github空间里就有这个项目的一个版本，允许做任何修改、推送，这是你自己的版本。
* 如果想把自己的修改贡献给社区，Github里点击pull requests
* 收到pull requests，检查后可以merge



