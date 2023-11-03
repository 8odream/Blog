---
title: tree-and-algorithm
date: 2023-11-01 21:39:45
tags: algorithm
---
## 树

树是图下的一个简单经典模型.树分为经典的二叉树和复杂的多叉树.二叉树就是一个最经典的例子:每一个节点下**至多**拥有两个叶子节点.

实例:

``` mermaid
graph TB

A((A))
B((B))
C((C))
D((D))
E((E))
F((F))
G((G))
A-->B-->D-->E
B-->G
D-->F
A-->C
```

其中,A为根节点.B和C都称为A的子节点.

## 树的表示

### 表格数组法

对于一个树,我们有多种方法表示,其中较为方便的有矩阵表示法和链表表示法.

例如,以下表为例(描述的就是上图),若左边的点能通往上边的点,则值为1,反之为0.

点|A|B|C|D|E|F|G
--|-|-|-|-|-|-|-
A| 0|1|1|0|0|0|0
B| 0|0|0|1|0|0|1
C| 0|0|0|0|0|0|0
D| 0|0|0|0|1|1|0
E| 0|0|0|0|0|0|0
F| 0|0|0|0|0|0|0
G| 0|0|0|0|0|0|0

缺点很明显,就是占用内存太大,n个元素需要用到n^2^大小的内存占用,非常不划算.

当然,这种方法也有其优点:可以表示更为复杂的图(无论单项还是双向,是否有环等)

### 指针法

这个方法很常见也很直观:就是将一个数据封装在一个包里,里面可以找到我们要的数据本体,也可以找到下一个链接的数据地址以便于找到下一个数据.用c语言可以用结构体来打包这个数据,用python可以用列表来模拟地址找到数据.以下给出c语言的实例:

``` C
#include<stdio.h>
#include<stdlib.h>

struct TreeData{
    int num;
    struct TreeData *next[2];   //定义指针域。每个数据最多包含两个子节点。如果只有一个节点，那么空节点可以定义为-1
};

int main(){
    struct TreeData tree[7];
    for (int i=0;i<7;i++){
        tree[i].num=i;
    }

    tree[0].next[0]=&tree[1],tree[0].next[1]=&tree[2];
    //对每个节点的指针域赋值，部分代码省略

    int r=tree[0].next[0]->num;  //例如，访问根节点的左节点的值
    printf("%d",r);
    system("pause");
    return 0;
}
```

## 搜索方法

### 二分法

二分法,就是在**有顺序**的一串数据里寻找需要的值.参考我们翻字典的时候,我们如果要找一个首字母为K的字词,我们不会从首页逐一翻页,而是可以快速先翻到靠近中间的位置来找,随后逐步缩小范围.当然,普通的二分法就是以1/2为中介值,左右逐次对半寻找.在特定场景下,我们也有带有偏移变量的中介值(例如当变量趋近于正态分布)来加速寻找.

### 深度搜索

简单理解,就是搜索时"一条路走到黑",触底后再反弹.我们一般遵循中序遍历的方式(根-左-右).例如,上面图中的树的检索顺序为:

``` mermaid
graph LR

A-->B-->D-->E-->F-->G-->C
```

这种搜索的应用场景常见于寻找需要的值时,一般需要遍历全部元素.
以下给出c语言的实例:

``` C
//下面的例子使用链表法表示树，并用于计算树的深度
#include<stdio.h>
#include<stdlib.h>
#include<stddef.h>

struct Node{
    int num;
    struct Node *next[2];   //定义指针域。每个数据最多包含两个子节点。如果只有一个节点，那么空节点可以定义为-1
};

void Search(struct Node *node,int *layer0){
    int layer1=*layer0+1,layer2=*layer0+1;
    if (node->next[0]){
        Search(node->next[0],&layer1);
    }
    if (node->next[1]){
        Search(node->next[0],&layer2);
    }
    *layer0=layer1>layer2?layer1:layer2;
}

int main(){
    int layer=0;
    //给定树
    struct Node tree[7];
    for (int i=0;i<7;i++){
        tree[i].num=i;
    }
    tree[0].next[0]=&tree[1];tree[0].next[1]=&tree[2];
    tree[1].next[0]=&tree[3];tree[1].next[1]=&tree[4];
    tree[2].next[0]=NULL;    tree[2].next[1]=NULL;
    tree[3].next[0]=&tree[5];tree[3].next[1]=&tree[6];
    tree[4].next[0]=NULL;    tree[4].next[1]=NULL;
    tree[5].next[0]=NULL;    tree[5].next[1]=NULL;
    tree[6].next[0]=NULL;    tree[6].next[1]=NULL;

    Search(&tree[0],&layer);
    printf("%d",layer);
    system("pause");
    return 0;
}
```

当然,还有更为经典的写法:

``` C
//给定结构体和预处理命令，略

void Search(struct Node *node,int *layer,int cnt){
    if(node==NULL){
        *layer=*layer>cnt?*layer:cnt;
        return;
    }
    cnt++;
    Search(node->next[0],layer,cnt);
    Search(node->next[1],layer,cnt);
}

int main(){
    //给定树,代码略
    int layer=0;
    Search(&tree[0],&layer,0);
    return 0;
}
```

### 广度搜索

广度搜索就是以层为方向,逐一遍历单层的各个数据,从而找出可能的"最短路径".经典的问题有最短公交换乘问题.

我们的做法是,遍历一层的数据时,将下一层的数据放入"需要被遍历"的"缓冲区".

以下给出Python的实例:

``` py3
tree=[[0,[1,2]],[1,[3,4]],[2,[-1,-1]],[3,[5,6]],[4,[-1,-1]],[5,[-1,-1]],[6,[-1,-1]]] #每个节点包含一个数据和一个模拟链表指针
process=[0] #将要运行的顺序,最先运行索引为0的节点

i=0
while not(tree[process[i]][1][0]==-1 and tree[process[i]][1][1]==-1):
    if tree[process[i]][1][0]!=-1:
        process.append(tree[process[i]][1][0])
    if tree[process[i]][1][1]!=-1:
        process.append(tree[process[i]][1][1])
    i+=1
#下面的代码将检查的节点数转换为层数
t=0
k=1
while(t<=i):
    t+=k
    k+=1
print(k-1,"层")
```
