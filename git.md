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

现在是空的，假如我把git.md文档放到目录下，再检查状态：

![l7Fxcd.png](https://s2.ax1x.com/2020/01/13/l7Fxcd.png)

检查到了这个文件，但提示没有提交。

### 4.2 暂存文件

我们可以用 git add 把它放到暂存区（staging area）：

    git add git.md 

若添加多个文件，可以这样

    git add file.txt file1.txt file3.txt

![l7kwE6.png](https://s2.ax1x.com/2020/01/13/l7kwE6.png)

### 4.3 提交
当我们用 git add 把所有想要跟踪的文件都放到缓存区后，就可以提交了。用下面的命令：

    git commit -m "Commit message"

双引号里是输入一些文字说明，记录本次提交做了哪些修改等。

![l7AdMj.png](https://s2.ax1x.com/2020/01/13/l7AdMj.png)

到这里，恭喜你已经成功的完成了项目的一次提交！

再次输入 git status 查看状态，显示 "nothing to commit, working tree clean"。此时，输入

    git log

能够看到提交记录。

![l7AXyd.png](https://s2.ax1x.com/2020/01/13/l7AXyd.png)

如果在路径下添加了一个新文件 test.md, 同时，git.md这个文件也发生了修改。我们再用 git status 查看状态：

![l7ZNRO.png](https://s2.ax1x.com/2020/01/13/l7ZNRO.png)

检查到一个文件被修改，一个新添加文件。下面提交这两个文件：

    git add git.md test.md
    git commit -m "modified git.md and test.md"

![l7Z7F0.png](https://s2.ax1x.com/2020/01/13/l7Z7F0.png)

如果要跟踪的文件很多，可以用

    git add .

全部添加到缓冲区。

### 4.4 版本回退
用 git log 可以查看提交记录。如果要回退到前面的版本，可以用命令：

    git checkout <commit-hash>

将 commit-hash 替换成在git log中显示的某个版本的码号。若要回到最新版本，输入命令

    git checkout master

## 5. 分支 (Branches)
分支可以解释为项目提交的独立时间线。使用Git，我们可以创建很多分支，实现不同版本的项目并行跟踪，不会影响项目的稳定版本（一般在master分支）。

### 5.1 创建分支
当创建一个仓库，开始提交文件，默认保存在master分支。用下面的命令可以创建一个新分支。

    git branch <new-branch-name>

![l7KKbQ.png](https://s2.ax1x.com/2020/01/13/l7KKbQ.png)

### 5.2 切换分支
执行下面命令：

    git checkout <branch-name>

切换到 branch-name 分支，如果是一个新分支，则引用当前版本的仓库。

![l7KLqg.png](https://s2.ax1x.com/2020/01/13/l7KLqg.png)

在新分支中，可以尝试一些新想法，不影响master分支。

### 5.3 合并分支
当测试成功后，把两个分支合并：

    git merge <branch-name>

把 branch-name 分支合并到当前分支。

### 5.4 删除分支

    git branch -d <branch-name>







