#define _CRT_SBCURE_NO_DEPRECATE
#include set
#include cmath
#include queue
#include stack
#include vector
#include string
#include cstdio
#include cstdlib
#include cstring
#include iostream
#include algorithm
#include functional

using namespace std;


int main()
{
    int x;
	queueint q;队列的定义
	while(scanf(%d,&x)!=EOF&&x0)
    {
        if(q.size()!=5)判断队列是否已满
        {
            q.push(x);入队
        }
        else
            cout队列已满，存入失败endl;
    }
	cout队列长：q.size()endl;访问队列中元素个数
	 if(q.size()==0)判断队列是否为空
        {
             cout空队列endl;
        }
	while(!q.empty())判断队列是否为空
	{
		coutq.front() ;访问队首
		q.pop();出队，删除队首，并不返回值，与栈的pop相似
	}
	return 0;
}
