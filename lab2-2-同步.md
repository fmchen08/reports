# 多线程与同步问题
[TOC]
## 线程
### Linux线程创建
Pthreads是POSIX标准定义的线程创建与同步API。编写多线程程序的第一步是创建新线程：

    #include <pthread.h>
    int pthread_create(
        pthread_t *             thread,
        const pthread_attr_t *  attr,
        void *                  (*start_routine)(void*),
        void *                  arg);

该函数有4个参数：thread、attr、start_routine 和 arg。
- thread是指向pthread_t结构类型的指针，我们将利用这个结构与该线程交互，所以要把它传入pthread_create(),以便将它初始化。
- attr用于指定该线程可能具有的属性。可以通过调用函数pthread_attr_init(&attr)初始化属性。
- 第三个参数是一个函数指针。除了传递线程标识符和线程属性外，还要传递函数名称start_routine，以便线程可以开始执行这个函数。
- arg是要传递给start_routine函数的参数。

**注意**：
- 所有的Pthreads程序都要包括头文件pthread.h
- 编译时要加上 -lpthread 
  
### 例1 创建一个线程
    
    #include <stdio.h>
    #include <pthread.h>
    #include <stdlib.h>

    int sum; //this data is shared by the threads
    void *runner(void *param); //threads call this function

    int main(int argc, char* argv[])
    {
        pthread_t tid;   	// the thread identifier
        pthread_attr_t attr;	// set of thread attributes
        
        if (argc!=2){
            fprintf(stderr, "usage: a.out <integer value>\n");
            return -1;
        }
        if(atoi(argv[1])<0){
            fprintf(stderr, "%d must be >=0\n", atoi(argv[1]));
        }

        // get the default attributes
        pthread_attr_init(&attr);
        // create the thread
        pthread_create(&tid, &attr, runner, argv[1]);
        // wait for the thread to exit
        pthread_join(tid, NULL);
        printf("sum = %d\n", sum);
        
        return 0;
    }

    void *runner(void *param)
    {
        int i, upper;
        upper = atoi(param);
        sum = 0;

        for(i=1; i<=upper; i++)
            sum += i;
        
        pthread_exit(0);
    }

### 例2 创建多个线程

    #define NUM_THREADS 10

    pthread_t workers[NUM_THREADS];

    //等待多个线程
    for (int i=0; i<NUM_THREADS; i++)
        pthread_join(workers[i], NULL);

### 例3 多线程并发访问共享的数据会破坏数据

    #include <stdio.h>
    #include <pthread.h>
    #include <stdlib.h>

    int max;
    int counter = 0; // shared data

    void *mythread(void *param)
    {
        char *letter = param;
        printf("%s begin\n", letter);
        int i;
        for(i=0; i<max; i++)
            counter = counter + 1;
        printf("%s done\n", letter);
        return NULL;
    }

    int main(int argc, char* argv[])
    {
        if(argc!=2)if (argc!=2){
                fprintf(stderr, "usage: a.out <loopcount>\n");
                return -1;
            }
            
        max = atoi(argv[1]);
        printf("main: begin(counter = %d)\n", counter);

        pthread_t p1, p2;  // the thread identifiers

        // create the thread
        pthread_create(&p1, NULL, mythread, "A");
        pthread_create(&p2, NULL, mythread, "B");

        // wait for the threads to exit
        pthread_join(p1, NULL);
        pthread_join(p2, NULL);

        printf("main: done\n (counter = %d)\n (should: %d)\n", counter, max *2);
        
        return 0;
    }

编译并运行该程序，改变输入参数的值，多试几次，观察它的行为。

![thread.PNG](https://i.loli.net/2020/04/01/EXH93zltpxo2GnF.png)

---
## 信号量
信号量是一个有整数值的对象，可以用两个函数来操作它。在POSIX标准中，是sem_wait()和sem_post()。首先要初始化信号量。

    #include <semaphore.h>
    sem_t s;
    sem_init(&s, 0, 1);

声明了一个信号量s，通过第三个参数，将它的值初始化为1。sem_init()的第二个参数是0，表示信号量是在**同一个进程**的多个线程共享的。
信号量初始化之后，我们可以调用sem_wait()或sem_post()与之交互。

    int sem_wait(sem_t *s){
        decrement the value of semaphore s by one
        wait if value of semaphore s is negative
    }

    int sem_post(sem_t *s){
        increment the value of semaphore s by one
        if there are one or more threads waiting, wake one
    }

信号量的值可以表示系统中剩余资源的个数，当它小于0时，这个值就是等待该资源的线程个数。

### 用法1：二值信号量（锁）
信号量的第一种用法：作为锁，把临界区用一对sem_wait()/sem_post()环绕。此时，信号量的初值应该是1。

    sem_t m;
    sem_init(&m, 0, 1);

    sem_wait(&m);
    // critical section here
    sem_post(&m);


### 用法2：计数信号量
实现对资源数量的管理。这种场景下，信号量用作**条件变量**。通常一个线程等待条件成立（资源数>0），另一个线程修改条件（释放资源）并发信号给等待线程。

---
## 生产者/消费者（有界缓冲区）问题
生产者/消费者问题也叫作有界缓冲区(bounded buffer)问题。这一问题最早由Dijkstra提出。假设有一个或多个生产者线程和一个或多个消费者线程。生产者把生成的数据项放入缓冲区；消费者从缓冲区取走数据项，以某种方式消费。

**把串行变成并行的一个简单策略**：把串行的工作分成几个步骤，每个步骤单独拿一个进程（线程）来做，它们彼此之间构成生产者和消费者的关系。

很多实际的系统中都会有这种场景。

(1) 在多线程的网络服务器中，一个生产者将HTTP请求放入工作队列（即有界缓冲区），消费线程从队列中取走请求并处理。
(2) 我们在使用管道命令连接不同程序的输出和输入时，也会使用有界缓冲区。例如：

    grep foo file.txt | wc -l 

这个例子并发执行了两个进程，grep进程从file.txt中查找包括“foo”的行，写到标准输出；shell把输出重定向到管道。管道的另一端是wc进程的标准输入，wc统计完行数后打印出结果。因此，grep是生产者，wc是消费者，他们之间是内核中的有界缓冲区。

### 问题分析
- 有没有临界资源？如果有，如何划分临界区？
- 需要定义哪些信号量？它们的初值怎么设置？
- 如何通过信号量操作实现生产者和消费者的合作（同步）？

### 回答
(1) 生产者和消费者线程共享缓冲区，因此缓冲区是临界资源。对缓冲区进行操作的部分代码就是临界区：即生产者"存"的动作和消费者"取"的动作。
(2) 三个信号量:
  - 互斥信号量mutex，初始化为1。作为锁，保护缓冲区。
  - 计数信号量empty，初始化为缓冲区的大小MAX，表示空格子的个数。作为条件变量，生产者要判断empty的值，只有当empty大于0时才能往缓冲区放数据。
  - 计数信号量full，初始化为0，表示有数据的格子的个数。作为条件变量，消费者要判断full的值，只有当full大于0时才能从缓冲区中取数据。
  
信号量定义和设置：
  
    sem_t mutex;
    sem_t empty;
    sem_t full;

    int main(int argc, char *argv[])
    {
        //...
        sem_init(&mutex, 0, 1);
        sem_init(&empty, 0, MAX);
        sem_init(&full, 0, 0);
        //...
    }

（3） 生产者和消费者线程的伪代码描述：

生产者线程：

    do{
        生产一个数据;
        sem_wait(&empty);
        sem_wait(&mutex);
        向缓冲区存一个数据; 
        sem_post(&mutex);
        sem_post(&full); 
    }while(true);
    

消费者线程：

    do{
        sem_wait(&full);
        sem_wait(&mutex);
        从缓冲区取一个数据; 
        sem_post(&mutex);
        sem_post(&empty); 
        处理这个数据;
    }while(true);
    