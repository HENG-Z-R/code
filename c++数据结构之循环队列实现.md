# C/C++数据结构之循环队列实现

**实现循环队列基本功能**



#### 循环队列实现
```
#define _CRT_SBCURE_NO_DEPRECATE
#include <set>
#include <cmath>
#include <queue>
#include <stack>
#include <vector>
#include <string>
#include <cstdio>
#include <cstdlib>
#include <cstring>
#include <iostream>
#include <algorithm>
#include <functional>


typedef struct queue_arr
{
    int * data;
    int front;
    int rear;
    int count;
} que;

//初始化队列
que * InitQueue()
{
//    que * q = (que *)malloc(sizeof(que));
    que * q =new (que);
    q->front = 0;
    q->rear = 0;
    q->count = 0;//可用于判断队空、队满
    return q;
}

//判断队满
int FullQueue(que * q)
{
    //设置队列长度为10
    if((q->rear+1)%10 == q->front)
        return 0;
    return 1;
}

//入队函数
int EnQueue(que * q, int data)
{
    if(FullQueue(q) == 0)
    {
        return 1;
    }
    else
    {
        q->data[q->rear] = data;
        q->rear = (q->rear+1)%10;
        q->count++;
        return 0;
    }
}

//出队函数
que * DelQueue(que * q, int data)
{
    que * del = q;
    int tmp = del->front,n = del->count;
    if(q->count == 0)//判断队空
        return q;


              del->front = (tmp+1)%10;
              del->count = n;
              return del;

        tmp = (tmp+1)%10;

    return q;
}

//遍历队列

void Display(que * q)
{
    int i =q->front;
    while(i != q->rear)
    {
        printf("%d ",q->data[i]);
        i = (i+1)%10;
    }
    if(q->count == 0)
        printf("队列为空！");
    printf("\n");
}

//测试代码
int main()
{
    que * q;
    int a,x;
    int L=0;
    q = InitQueue();
    printf("1.输出、2.入队、3.出队、4.求队列长度、5.退出，请输入操作对应序号\n");
    while(scanf("%d",&a)!=5)
    {
        if(a==1)
        {
             printf("队列成员为：");
            Display(q);
        }
        if(a==2)
        {
            printf("需要入队的数是：");
            scanf("%d",&x);
            if(EnQueue(q,x) == 1)
                printf("队满，不能入队！\n");
            else
            {
                printf("数字 %d 入队后，队列成员为：",x);
                Display(q);
                L++;
            }

        }
        if(a==3)
        {
            printf("开始出队\n");
                DelQueue(q,x);
                printf("出队后，队列成员为：");
                Display(q);
            if(L>=0)
                L--;
        }
        if(a==4)
        {
            printf("队列长度为：%d\n",L);

        }
    }
    return 0;
}

```

