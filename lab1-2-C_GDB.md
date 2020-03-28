# Linux下的C语言编程与调试
## 1. Unbuntu 18.04更改apt成阿里云软件源
### 
（1）首先备份Ubuntu系统的官方源文件。打开Ubuntu的命令终端，进入源文件 sources.list 所在的目录，然后执行备份命令，执行 sudo cp sources.list sources.list.backup 对源文件内容进行备份。
  
    cd /etc/apt
    sudo cp sources.list sources.list.backup

（2）将 sources.list 源文件内容替换成：

    deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
    deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
    deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
    deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
    deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
    deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
    deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
    deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
    deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
    deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse

这里，要用 

    sudo gedit sources.list

打开 -> 编辑 -> 保存 -> 关闭文件。

（3）更新源

    sudo apt-get update


## 2. 安装GCC

    sudo apt-get install gcc

安装过程中，如果遇到 Could not get lock /var/lib/dpkg/lock-frontend -open(11: Resource tenporarily unavailable)错误，是因为有之前的apt进程没退出，解决方法是删除锁定文件

    sudo rm /var/lib/dpkg/lock-frontend
    sudo rm /var/lib/dpkg/lock


## 3. 命令行参数：int argc, char* argv[]
So far, all the programs we have written can be run with a single command. For example, if we compile an executable called myprog, we can run it from within the same directory with the following command at the GNU/Linux command line: 

    ./myprog

However, what if you want to pass information from the command line to the program you are running? Consider a more complex program like GCC. To compile the hypothetical myprog executable, we type something like the following at the command line: 

    gcc -o myprog myprog.c

The character strings -o, myprog, and myprog.c are all arguments to the gcc command. (Technically gcc is an argument as well, as we shall see.)

Command-line arguments are very useful. After all, C functions wouldn't be very useful if you couldn't ever pass arguments to them -- adding the ability to pass arguments to programs makes them that much more useful. In fact, all the arguments you pass on the command line end up as arguments to the main function in your program.

Up until now, the skeletons we have used for our C programs have looked something like this: 

    #include <stdio.h>

    int main()
    {

        return 0;
    }

From now on, our examples may look a bit more like this: 

    #include <stdio.h>

    int main (int argc, char *argv[])
    {

        return 0;
    }

As you can see, main now has arguments. The name of the variable argc stands for "argument count"; argc contains the number of arguments passed to the program. The name of the variable argv stands for "argument vector". A vector is a one-dimensional array, and argv is a one-dimensional array of strings. Each string is one of the arguments that was passed to the program.

For example, the command line 

    gcc -o myprog myprog.c

would result in the following values internal to GCC:


    argc
    4 
    argv[0]
    gcc 
    argv[1]
    -o 
    argv[2]
    myprog 
    argv[3]
    myprog.c

As you can see, the first argument (argv[0]) is the name by which the program was called, in this case gcc. Thus, there will always be at least one argument to a program, and argc will always be at least 1.

The following program accepts any number of command-line arguments and prints them out: 

    #include <stdio.h>

    int main (int argc, char *argv[])
    {
        int count;

        printf ("This program was called with \"%s\".\n",argv[0]);

        if (argc > 1)
        {
            for (count = 1; count < argc; count++)
            {
                printf("argv[%d] = %s\n", count, argv[count]);
            }
        }
        else
            {
                printf("The command had no other arguments.\n");
            }

        return 0;
    }
If you name your executable fubar, and call it with the command ./fubar a b c, it will print out the following text: 

    This program was called with "./fubar".

    argv[1] = a
    argv[2] = b
    argv[3] = c

## 4. GDB
GNU Project Debugger
是一个命令行工具。
退出：quit(q)
