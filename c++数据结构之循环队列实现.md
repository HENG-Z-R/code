# C/C++���ݽṹ֮ѭ������ʵ��

**ʵ��ѭ�����л�������**



#### ѭ������ʵ��
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

//��ʼ������
que * InitQueue()
{
//    que * q = (que *)malloc(sizeof(que));
    que * q =new (que);
    q->front = 0;
    q->rear = 0;
    q->count = 0;//�������ж϶ӿա�����
    return q;
}

//�ж϶���
int FullQueue(que * q)
{
    //���ö��г���Ϊ10
    if((q->rear+1)%10 == q->front)
        return 0;
    return 1;
}

//��Ӻ���
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

//���Ӻ���
que * DelQueue(que * q, int data)
{
    que * del = q;
    int tmp = del->front,n = del->count;
    if(q->count == 0)//�ж϶ӿ�
        return q;


              del->front = (tmp+1)%10;
              del->count = n;
              return del;

        tmp = (tmp+1)%10;

    return q;
}

//��������

void Display(que * q)
{
    int i =q->front;
    while(i != q->rear)
    {
        printf("%d ",q->data[i]);
        i = (i+1)%10;
    }
    if(q->count == 0)
        printf("����Ϊ�գ�");
    printf("\n");
}

//���Դ���
int main()
{
    que * q;
    int a,x;
    int L=0;
    q = InitQueue();
    printf("1.�����2.��ӡ�3.���ӡ�4.����г��ȡ�5.�˳��������������Ӧ���\n");
    while(scanf("%d",&a)!=5)
    {
        if(a==1)
        {
             printf("���г�ԱΪ��");
            Display(q);
        }
        if(a==2)
        {
            printf("��Ҫ��ӵ����ǣ�");
            scanf("%d",&x);
            if(EnQueue(q,x) == 1)
                printf("������������ӣ�\n");
            else
            {
                printf("���� %d ��Ӻ󣬶��г�ԱΪ��",x);
                Display(q);
                L++;
            }

        }
        if(a==3)
        {
            printf("��ʼ����\n");
                DelQueue(q,x);
                printf("���Ӻ󣬶��г�ԱΪ��");
                Display(q);
            if(L>=0)
                L--;
        }
        if(a==4)
        {
            printf("���г���Ϊ��%d\n",L);

        }
    }
    return 0;
}

```

