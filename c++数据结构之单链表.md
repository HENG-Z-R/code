# 欢迎使用 Markdown在线编辑器 MdEditor

**Markdown是一种轻量级的「标记语言」**



#### 链表功能实现
```
#include <iostream>

using namespace std;

typedef struct LNode
{
	int data;
	struct LNode *next;
}LNode,*LinkList;

void CreateList(LinkList &L,int n)
{
    int i;
    LNode *r,*p;
	L=new LNode;
	L->next=NULL;
	r=L;
	cout<<"请输入元素:\n";
	for(i=0;i<n;++i)
	{
		p=new LNode;
		cin>>p->data;
		p->next=NULL;
		r->next=p;
		r=p;
	}
}

void display(LinkList L)
{
	LNode *p;
	p=L->next;
	cout<<"{";
	while(p)
	{
	    cout<<p->data<<" ";
        p=p->next;
    }
	cout<<"}"<<endl;
}

void Insert(LinkList &L,int n)
{

    LNode *q,*p,*head;
    head=L->next;
    n=n-2;
    while(n--)
    {
        head=head->next;
    }
	cout<<"请输入元素:\n";
		q=new LNode;
		cin>>q->data;
		p=head->next;
		head->next=q;
		q->next=p;
}

void Delete(LinkList &head,int num)
{
	LNode *p1, *p2;
	p2 = new LNode;
	p1 = head;

	while (num != p1->data && p1->next != NULL)
	{
		p2 = p1;
		p1 = p1->next;
	}
	if (num == p1->data)
	{
		if (p1 == head)
		{
			head = p1->next;
			delete p1;
		}
		else
		{
			p2->next = p1->next;
			delete p1;
		}
	}
	else
	{
		cout << num << "没找到" << endl;
	}

}


int main()
{
    int n;
    LNode *La,*Lc;
    Lc=new LNode;
	Lc->next=NULL;

	cout<<"链表实现"<<endl;
	cout<<"请输入需要建立链表的长度"<<endl;
    cin>>n;
    CreateList(La,n);
    display(La);

    cout<<"功能实现：插入"<<endl;
    cout<<"请输入需要插入的位置"<<endl;
    cin>>n;
    Insert(La,n);
    display(La);

    cout<<"功能实现：删除"<<endl;
    cout<<"请输入需要删除的元素"<<endl;
    cin>>n;
    Delete(La,n);
    display(La);
    return 0;
}

```
#### 通过一趟遍历在单链表确定最大的结点
```
#include <iostream>

using namespace std;

typedef struct LNode
{
int data;
struct LNode *next;
}LNode,*LinkList;

void CreateList(LinkList &L,int n)
{
    int i;
    LNode *r,*p;
L=new LNode;
L->next=NULL;
r=L;
cout<<"请输入元素：\n";
for(i=0;i<n;++i)
{
p=new LNode;
cin>>p->data;
p->next=NULL;
r->next=p;
r=p;
}
}

void MAX(LinkList &L,int n)
{
    int M,i,flag;
    LNode *p=L->next;
    M=p->data;
    flag=0;
    for(i=0;i<n;++i)
{
if(p->data>M)
        {
            M=p->data;
            flag=i+1;
        }

        p=p->next;
}
cout<<"第"<<flag<<"个结点的值最大，"<<"值为"<<M<<endl;

}

int main()
{
    int n;
    LNode *la;

    cin>>n;
    CreateList(la,n);
    MAX(la,n);
    return 0;
}

```

#### 求A和B两个单链表表示的集合的并集
```
#include <iostream>

using namespace std;

typedef struct LNode
{
int data;
struct LNode *next;
}LNode,*LinkList;

void CreateList(LinkList &L,int n)
{
    int i;
    LNode *r,*p;
L=new LNode;
L->next=NULL;
r=L;
cout<<"请输入元素\n";
for(i=0;i<n;++i)
{
p=new LNode;
cin>>p->data;
p->next=NULL;
r->next=p;
r=p;
}
}

void display(LinkList L)
{
LNode *p;
p=L->next;
cout<<"{";
while(p)
{cout<<p->data<<" ";
p=p->next;}
cout<<"}"<<endl;
}



void bingji(LinkList &La,LinkList &Lb)
{
    LNode *pa;
    LNode *pb;
    LNode *p,*s;
    pa=La->next;pb=Lb->next;
    while(pa&&pb)
    {

        s=new LNode;
        if (pa->data<pb->data)
        {
            if(pa->next!=NULL)
            {
                if(pa->next->data>pb->data)
                {
                    s->data=pb->data;
                    p=pa->next;
                    pa->next=s;
                    s->next=p;
                    pa=pa->next;
                    pb=pb->next;
                }
                else
                {
                    pa=pa->next;
                }
            }
            else
            {
                s->data=pb->data;
                pa->next=s;
                s->next=NULL;
                pa=pa->next;
                pb=pb->next;
            }
        }
        else
        {
            if (pa->data>pb->data)
            {
                s->data=pa->data;
                pa->data=pb->data;
                p=pa->next;
                pa->next=s;
                s->next=p;
            }
            else
            {
                pb=pb->next;
            }
        }

    }

    while(!pa&&pb)
    {
        s=new LNode;
        s->data=pb->data;
        pa->next=s;
        s->next=NULL;
        pa=pa->next;
        pb=pb->next;
    }

    delete Lb;
}


int main()
{
    int n,m;
    LNode *La,*Lb;

    cin>>n;
    CreateList(La,n);
    cin>>m;
    CreateList(Lb,m);
    bingji(La,Lb);
    display(La);
    return 0;
}

```


#### 求A和B两个单链表表示的集合的并集
```
#include <iostream>

using namespace std;

typedef struct LNode
{
int data;
struct LNode *next;
}LNode,*LinkList;

void CreateList(LinkList &L,int n)
{
    int i;
    LNode *r,*p;
L=new LNode;
L->next=NULL;
r=L;
cout<<"请输入元素:\n";
for(i=0;i<n;++i)
{
p=new LNode;
cin>>p->data;
p->next=NULL;
r->next=p;
r=p;
}
}

void display(LinkList L)
{
LNode *p;
p=L->next;
cout<<"{";
while(p)
{
    cout<<p->data<<" ";
        p=p->next;
    }
cout<<"}"<<endl;
}



LinkList nixu(LinkList &list)
{
LinkList p,q,head;
head=list->next;
p=NULL;
while(head)
{
q=head;
head=q->next;
q->next=p;
        p=q;
}
p=new LNode;
    p->next=q;
list=p;
return list;
}

int main()
{
    int n;
    LNode *La,*Lc;

    Lc=new LNode;
Lc->next=NULL;
    cin>>n;
    CreateList(La,n);
    nixu(La);
    display(La);
    return 0;
}

```

