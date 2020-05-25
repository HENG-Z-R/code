# c++数据结构之栈与队列

怎样判断一个人是否是程序员？答：问他push的反义词是什么。回答pull的是普通人，回答pop的才是程序员。

#### 栈
```
#include<iostream>
#include<stack>//包含栈的头文件 
using namespace std;
int main()
{
	stack<int> s;//栈的定义 
	for(int i=0;i<10;i++)
	{
		s.push(i);//压栈 
	} 
	cout<<s.size()<<endl;//访问栈中元素个数
	while(!s.empty())//判断栈是否为空 
	{
		cout<<s.top()<<" ";//访问栈顶 
		s.pop();//弹栈，弹栈只是删除栈顶，并不返回栈顶，通常与top()连用 
	}
	return 0;
}

```
#### 队列

```
#include<iostream>
#include<queue>//包含队列的头文件 
using namespace std;

int main()
{
	queue<int> q;//队列的定义 
	for(int i=0;i<10;i++)
	{
		q.push(i);//入队 
	}
	cout<<q.size()<<endl;//访问队列中元素个数 
	cout<<"队首："<<q.front()<<endl;
	cout<<"队尾："<<q.back()<<endl;
	while(!q.empty())//判断队列是否为空 
	{
		cout<<q.front()<<" ";//访问队首 
		q.pop();//出队，删除队首，并不返回值，与栈的pop相似 
	}
	return 0;
}

```