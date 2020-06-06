# c++数据结构之二叉树实现（递归）

**输入时自动排序：左儿子 < 父节点 < 右儿子**




> 说明：代码主要参考TheSevenSky的博客
[普通链接](https://blog.csdn.net/qq_42011541/article/details/80547098?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.nonecase)。






#### 完整代码
```
#include <cstdlib>
#include <stdio.h>

typedef struct node{ //树的结点
    int data;
    struct node* left;
    struct node* right;
} Node;

typedef struct { //树根
    Node* root;
} Tree;

void insert(Tree* tree, int value)//创建树
{
   // Node* node=(Node*)malloc(sizeof(Node));//创建一个节点
    Node* node=new (Node);
    node->data = value;
    node->left = NULL;
    node->right = NULL;
    if (tree->root == NULL)//判断树是不是空树
    {
        tree->root = node;
    }
    else {//不是空树
        Node* temp = tree->root;//从树根开始
        while (temp != NULL)
        {
            if (value < temp->data)//小于就进左儿子
            {
                if (temp->left == NULL)
                {
                    temp->left = node;
                    return;
                }
                else {//继续判断
                    temp = temp->left;
                }
            }
            else {//否则进右儿子

                if (temp->right == NULL)
                {
                    temp->right = node;
                    return;
                }
                else {//继续判断
                    temp = temp->right;
                }
            }
        }
    }
    return;
}

void preorder(Node* node)//树的先序遍历
{
    if (node != NULL)
    {
        printf("%d ",node->data);
        preorder(node->left);
        preorder(node->right);
    }
}

void inorder(Node* node)//树的中序遍历
{
    if (node != NULL)
    {
        inorder(node->left);
        printf("%d ",node->data);
        inorder(node->right);
    }
}

void postorder(Node* node)//树的后序遍历
{
    if (node != NULL)
    {
        postorder(node->left);
        postorder(node->right);
        printf("%d ",node->data);
    }
}

int main()
{
    Tree tree;
    tree.root = NULL;//创建一个空树
    int n;
    printf("输入想要创建的二叉树的长度:\n");
    scanf("%d",&n);
    printf("创建二叉树:\n");
    for (int i = 0; i < n; i++)//输入n个数并创建这个树
    {
        int temp;
        scanf("%d",&temp);
        insert(&tree, temp);
    }

    printf("先根遍历\n");
    preorder(tree.root);//先序遍历
    printf("\n");

    printf("中根遍历\n");
    inorder(tree.root);//中序遍历
    printf("\n");

    printf("后根遍历\n");
    postorder(tree.root);//后序遍历
    printf("\n");

    getchar(); getchar();
    return 0;
}

```

