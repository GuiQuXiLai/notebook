# linux下出现undefined reference to pthread_create

## 问题

刚刚学习pthread_create这个函数，复制[pthread_create()函数：创建线程]([pthread_create()函数：创建线程 (biancheng.net)](http://c.biancheng.net/view/8607.html))的一个案例执行。

```c
#include <stdio.h>
#include <unistd.h>   //调用 sleep() 函数
#include <pthread.h>  //调用 pthread_create() 函数

void *ThreadFun(void *arg)
{
    if (arg == NULL) {
        printf("arg is NULL\n");
    }
    else {
        printf("%s\n", (char*)arg);
    }
    return NULL;
}

int main()
{
    int res;
    char * url = "http://c.biancheng.net";
    //定义两个表示线程的变量（标识符）
    pthread_t myThread1,myThread2;
    //创建 myThread1 线程
    res = pthread_create(&myThread1, NULL, ThreadFun, NULL);
    if (res != 0) {
        printf("线程创建失败");
        return 0;
    }
    sleep(5);  //令主线程等到 myThread1 线程执行完成
    
    //创建 myThread2 线程
    res = pthread_create(&myThread2, NULL, ThreadFun,(void*)url);
    if (res != 0) {
        printf("线程创建失败");
        return 0;
    }
    sleep(5); // 令主线程等到 mythread2 线程执行完成
    return 0;
}
```

直接出现以下问题

![image-20221031161410695](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221031161410695.png)

## 问题原因

`pthread`库不是linux系统默认的库，连接时需要使用静态库`libpthread.a`，所以在使用`pthread_create()`创建线程时，需要链接该库。

## 问题解决

在编译中要加`-lpthread参数`， `demo.c`为源文件，不要忘了加上头文件`#include<pthread.h>`

```bash
gcc demo.c -o demo -lpthread
```

**执行结果**

![image-20221031162224977](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221031162224977.png)