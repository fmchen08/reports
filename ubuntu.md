# 实验1 Linux初体验
## 1. 虚拟机安装 Ubuntu18.04 LTS
- 下载Ubuntu18.04 LTS，官网速度慢，用网易镜像
  http://mirrors.163.com/ubuntu-releases/18.04/
  ubuntu-18.04.4-desktop-amd64.iso
- 下载安装wmware workstation
  VMware-workstation-full-14.0.0.24051.exe
- 新建虚拟机，并安装ubuntu系统，参考PPT

## 2. Linux命令
### 2.1 文件与目录管理
- pwd：显示当前目录
- ls：文件与目录的查看
- cd: 切换目录

      $ cd Downloads  #进入Downloads目录
      $ cd ..         #退回上一级目录
      $ cd /          #进入根目录
      $ ls            #查看根目录的内容
      $ cd home       
      $ ls            #能看到用户名
      $ cd cfm        #回到用户目录
      $ pwd           #显示当前目录\

- mkdir：建立一个新目录
- rmdir：删除一个空目录

      $ mkdir os-lab 
      $ cd os-lab
      $ mkdir lab1
      $ cd lab1

- touch: 新建文件
- cp：复制
- rm：删除
- mv：移动

      $ touch hello.c             #新建一个文件
      $ ls
      $ cp hello.c hello_copy.c   #复制文件
      $ ls
      $ rm hello_copy.c           #删除文件
      $ ls
      $ cp hello.c /home/cfm/Downloads  #将文件复制到其他目录
      $ ls
      $ cd ..                     #回到用户目录
      $ cd ..
      $ cd Downloads              #进入Downloads目录
      $ ls                        #查看是否复制成功
      $ rm hello.c                #删除该文件
      $ cd ..                     #回到用户目录
  
  如果目录不是空的，不能用rmdir删除目录，这时要用 rm -r 

      $ cd os-lab/lab1            #进入lab1目录
      $ ls                        #检查是否有文件
      $ cd ..                     #回到上一级目录
      $ rmdir lab1                #rmdir: failed to remove 'lab1': Directory not empty
      $ rm -r lab1                #成功删除lab1目录

### 2.2 man命令
先来了解下Linux有多少命令？在命令行模式下，你可以输入g之后连续按下两个[Tab][Tab]，看看总共有多少以g开头的命令可以让你用。这么多命令怎么记住呢？你可以去问问man，man是manual的简写。

      $ man ls

一般这样查看：
（1）先查看NAME部分，大概了解这个数据的意思；
（2）再详看下DESCRIPTION，这个部分会提到很多相关的数据与使用时机，学到很多小细节；
（3）如果这个命令已经比较熟悉了，直接看OPTIONS，查看每个选项的意义，这样就可以执行比较详细的命令内容；
（4）最后，SEE ALSO告诉我们还有哪些相关的东西可以使用。

### 2.3 文件权限与目录配置
Linux最优秀的地方之一就在于它的多用户多任务环境。为了让各个用户具有保密的文件数据，文件权限管理就变得很重要了。Linux一般将文件可读写的身份分为三个类别，分别是：拥有者（owner），所属组群（group），其他人（others），且三种身份各有读（read）、写（write）、执行（execute）等权限。
#### 2.3.1 Linux文件属性
  
      ls -al    #列出所有文件的详细权限与属性

![8PbXdS.png](https://s2.ax1x.com/2020/03/10/8PbXdS.png)

- 第1栏：文件的类型与权限，共10个字符。
  - 第1个字符代表这个文件是目录、文件、或链接文件等。[d]为目录，[-]为文件，[l]为链接文件(类似windows下的快捷方式)。
  - 接下来的字符以三个为一组，且均为[rwx]三个参数的组合。其中[r]代表可读，[w]代表可写，[x]代表可执行。要注意的是，这三个权限的位置不会改变，如果没有权限，就会出现[-]。
  - 第一组为文件拥有者可具备的权限，第二组为加入此用户组的账号的权限，第三组为非本人且没有加入本用户组的其他账号的权限。
  
- 第2栏表示有多少文件名链接到此节点
- 第3栏表示这个文件或目录的拥有者账号
- 第4栏表示这个文件的所属用户组
- 第5栏为这个文件的大小
- 第6栏为这个文件的创建日期或最近的修改日期
- 第7栏为文件名，如果文件名前多一个[.]，表示这个文件为隐藏文件。
#### 2.3.2 修改文件属性与权限
- chgrp：修改文件所属用户组
- chown：修改文件拥有者
- chmod：修改文件的权限
  
数字类型修改文件权限：r(4)、w(2)、x(1)
rwx = 7, rw- = 6, r-- = 4

      $ chmod 777 .bashrc   #权限为-rwxrwxrwx

## 3. 认识与学习Bash Shell
### 3.1 什么是Shell？
管理整个计算机的是操作系统内核，一般用户通过Shell来跟内核沟通。Shell为用户使用操作系统提供了一个操作界面。

### 3.2 为什么要学习命令行模式的Shell？
- 几乎各家Linux发行版使用的bash都是一样的。
- 远程管理：命令行模式速度快。
- Shell脚本编程管理系统十分方便。
  
### 3.3 Bash的功能
- 历史命令(history): [上下键] 就可以找到前后的命令。这些命令都在家目录的.bash_history中记录着。
- 命令与文件补全功能：[Tab]
- 命令别名
- 任务管理、前台、后台控制：如[Ctrl+C]结束正在运行的程序
- 程序化脚本：将常需要执行的连续命令写成一个文件
- 通配符：*

      $ ls -l o*    # 列出当前目录下o开头的文件

### 3.4 输出重定向与管道命令




### 3.5 Shell脚本编程




## 3. Linux终端常用快捷键
- Ctrl+c 结束正在运行的程序
- Ctrl+d 结束输入或退出shell
- Ctrl+s 暂停屏幕输出【锁住终端】
- Ctrl+q 恢复屏幕输出【解锁终端】
- Ctrl+l 清屏
- Ctrl+a 切换到命令行开始
- Ctrl+e 切换到命令行末尾


