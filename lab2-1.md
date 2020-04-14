# Linux多进程编程
## 编写一个打开文件的程序（使用open()系统调用），然后调用fork()创建一个新进程。设计实验回答以下问题：
- 子进程和父进程都可以访问open()返回的文件描述符吗？
- 当它们并发写入文件时（使用write()系统调用），会发生什么？
- 如何保证子进程始终先写？你能否不在父进程调用wait()而做到这一点呢？
- 在父进程中使用wait()，等待子进程完成。wait()返回什么？如果你在子进程中使用wait()会发生什么？

提示：

（1）可能用到的头文件


    #include <stdio.h>
    #include <stdlib.h>
    #include <unistd.h>
    #include <sys/wait.h>
    #include <fcntl.h>
    #include <string.h>

（2）open()系统调用的例子:

    int fid;
    fid = open(“./out”, O_CREAT | O_WRONLY | O_TRUNC, S_IRWXU);

（3）使用man 2查询系统调用的用法，如 

    man 2 write
    man 2 open

---
## 文件描述符
### 简介
文件描述符在形式上是一个非负整数。实际上，**它是一个索引值，指向内核为每一个进程所维护的该进程打开文件的记录表**。当程序打开一个现有文件或者创建一个新文件时，内核向进程返回一个文件描述符。

习惯上，标准输入(standard input)的文件描述符是 0，标准输出(standard output)是 1，标准错误(standard error)是 2。POSIX 定义了 STDIN_FILENO、STDOUT_FILENO 和 STDERR_FILENO 来代替 0、1、2。这三个符号常量的定义位于头文件 unistd.h。

文件描述符的有效范围是 0 到 OPEN_MAX。一般来说，每个进程最多可以打开 64 个文件(0 - 63)。对于 FreeBSD 5.2.1、Mac OS X 10.3 和 Solaris 9 来说，每个进程最多可以打开文件的多少取决于系统内存的大小，int 的大小，以及系统管理员设定的限制。Linux 2.4.22 强制规定最多不能超过 1,048,576。

文件描述符是由无符号整数表示的句柄，进程使用它来标识打开的文件。文件描述符与包括相关信息(如文件的打开模式、文件的位置类型、文件的初始类型等)的文件对象相关联，这些信息被称作文件的上下文。

### 如何创建文件描述符
- 通过open或create获取。
- 通过从父进程继承。

后一种方法允许子进程同样能够访问由父进程使用的文件。文件描述符对于每个进程一般是唯一的。当用fork创建某个子进程时，该子进程会获得其父进程所有文件描述符的副本，这些文件描述符在执行fork时打开。对于每个进程，操作系统内核在u_block结构中维护文件描述符表，所有的文件描述符都在该表中建立索引。

---
### 1. 子进程和父进程都可以访问open()返回的文件描述符吗？

    #include <stdio.h>
    #include <stdlib.h>
    #include <unistd.h>
    #include <sys/wait.h>
    #include <fcntl.h>
    #include <string.h>

    int main()
    {
        //在当前路径打开一个文件，文件名为out	
        int fid;	
        fid = open("./out", O_CREAT | O_WRONLY | O_TRUNC, S_IRWXU); 
        
        pid_t rc = fork(); /*创建一个子进程*/
        
        if(rc < 0)
        {
            fprintf(stderr, "fork failed\n");
            exit(1);
        }
        else if(rc == 0) /*子进程*/
        {
            char* str1 = "Child process.\n";
            write(fid, str1, strlen(str1));
        }
        else /*父进程*/
        {                  
            char* str2 = "Parent process.\n";
            write(fid, str2, strlen(str2));
        }

        return 0;
    }


运行结果

    cfm@cfm-virtual-machine:~/os-lab/lab2$ gcc ex2.c -o ex2
    cfm@cfm-virtual-machine:~/os-lab/lab2$ ./ex2
    cfm@cfm-virtual-machine:~/os-lab/lab2$ cat out
    Parent process.
    Child process.

out文件中既有父进程写的内容，也有子进程写的内容，说明两个进程都可以访问open()返回的文件描述符。

### 2. 当它们并发写入文件时（使用write()系统调用），会发生什么？
**测试1**：父进程写完子进程写？子进程写完父进程写？

前面程序的结果是父进程先写，子进程后写。如果在父进程分支里，写文件之前加上 

    sleep(1);

就可以使子进程先写，父进程后写。

**测试2**：可否交替进行？

**设计**：写多行文本，子进程和父进程速度不同。

    #include <stdio.h>
    #include <stdlib.h>
    #include <unistd.h>
    #include <sys/wait.h>
    #include <fcntl.h>
    #include <string.h>

    #define N 10

    int main()
    {
        int fid;		
        fid = open("./out", O_CREAT | O_WRONLY | O_TRUNC, S_IRWXU);
        
        pid_t rc = fork();
        
        if(rc < 0)
        {
            fprintf(stderr, "fork failed\n");
            exit(1);
        }
        else if(rc == 0)
        {
            int j;
            char* str1 = "Child process.\n";
            
            for (j=0; j<N; j++)
            {      	
                write(fid, str1, strlen(str1));
              //sleep(0.0001);   /*子进程写的速度快些*/
            }
        }
        else
        {
    //		printf("%d\n", wait(NULL));
                    
            int i;
            char* str2 = "Parent process.\n";
        
            for (i = 0; i<N; i++)
            {	
                write(fid, str2, strlen(str2));
                sleep(0.2);     /*父进程写的速度慢些*/
            }
        }

        return 0;
    }


**结果**：
若父进程每写一行后sleep 0.2s，子进程不sleep，结果为：

    Parent process.
    Child process.
    Child process.
    Child process.
    Child process.
    Child process.
    Child process.
    Child process.
    Child process.
    Child process.
    Child process.
    Parent process.
    Parent process.
    Parent process.
    Parent process.
    Parent process.
    Parent process.
    Parent process.
    Parent process.
    Parent process.

若父进程每写一行后sleep 0.2s，子进程每写一行后sleep 0.1s，结果为：

    Parent process.
    Child process.
    Parent process.
    Child process.
    Parent process.
    Child process.
    Parent process.
    Child process.
    Parent process.
    Child process.
    Parent process.
    Child process.
    Parent process.
    Child process.
    Parent process.
    Child process.
    Parent process.
    Child process.
    Parent process.
    Child process.

说明父进程和子进程是并发执行的，可以交替的对同一个文件写数据。执行哪个进程取决于CPU调度情况。


### 3. 如何保证子进程始终先写？你能否不在父进程调用wait()而做到这一点呢？

在父进程中调用wait(NULL)，可以保证子进程先写。

如果不调用wait(), 在父进程分支里，写文件之前加上 

    sleep(1);

让父进程先阻塞一段时间，也可以使子进程先写，父进程后写。

### 4. 在父进程中使用wait()，等待子进程完成。wait()返回什么？如果你在子进程中使用wait()会发生什么？

    #include <stdio.h>
    #include <stdlib.h>
    #include <unistd.h>
    #include <sys/wait.h>
    #include <fcntl.h>
    #include <string.h>

    #define N 10

    int main()
    {
        int fid;		
        fid = open("./out", O_CREAT | O_WRONLY | O_TRUNC, S_IRWXU);
        
        pid_t rc = fork();
        
        if(rc < 0)
        {
            fprintf(stderr, "fork failed\n");
            exit(1);
        }
        else if(rc == 0)
        {
            printf("Child pid = %d\n", getpid());
            printf("Child wait = %d\n", wait(NULL));

            int j;
            char* str1 = "Child process.\n";
            for (j=0; j<N; j++)
            {      	
                write(fid, str1, strlen(str1));
                sleep(0.1);
            }
        }
        else
        {
            printf("Parent wait = %d\n", wait(NULL));
                    
            int i;
            char* str2 = "Parent process.\n";
        
            for (i = 0; i<N; i++)
            {	
                write(fid, str2, strlen(str2));
                sleep(0.2);
            }
        }


        return 0;
    }

**结果**

    Child pid = 3598
    Child wait = -1
    Parent wait = 3598

因此父进程里的wait()返回值为子进程的id，子进程里调用wait()返回-1。