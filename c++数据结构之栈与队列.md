# c++���ݽṹ֮ջ�����

�����ж�һ�����Ƿ��ǳ���Ա��������push�ķ������ʲô���ش�pull������ͨ�ˣ��ش�pop�Ĳ��ǳ���Ա��

#### ջ
```
#include<iostream>
#include<stack>//����ջ��ͷ�ļ� 
using namespace std;
int main()
{
	stack<int> s;//ջ�Ķ��� 
	for(int i=0;i<10;i++)
	{
		s.push(i);//ѹջ 
	} 
	cout<<s.size()<<endl;//����ջ��Ԫ�ظ���
	while(!s.empty())//�ж�ջ�Ƿ�Ϊ�� 
	{
		cout<<s.top()<<" ";//����ջ�� 
		s.pop();//��ջ����ջֻ��ɾ��ջ������������ջ����ͨ����top()���� 
	}
	return 0;
}

```
#### ����

```
#include<iostream>
#include<queue>//�������е�ͷ�ļ� 
using namespace std;

int main()
{
	queue<int> q;//���еĶ��� 
	for(int i=0;i<10;i++)
	{
		q.push(i);//��� 
	}
	cout<<q.size()<<endl;//���ʶ�����Ԫ�ظ��� 
	cout<<"���ף�"<<q.front()<<endl;
	cout<<"��β��"<<q.back()<<endl;
	while(!q.empty())//�ж϶����Ƿ�Ϊ�� 
	{
		cout<<q.front()<<" ";//���ʶ��� 
		q.pop();//���ӣ�ɾ�����ף���������ֵ����ջ��pop���� 
	}
	return 0;
}

```