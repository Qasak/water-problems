# water-problems

水题/leetcode高频题



### 1

有一个10数组，将位置为0的值改成1

要求，该位置左右两侧都为1

请问，能写多少个1？

```c++

#include<iostream>
#include <string.h>
using namespace std;
int a[1<<17];
int cnt = 0;
int n;
int func(int a[]) {
    for(int i=1;i<=n;i++) {
        if(a[i]==0&&a[i-1]!=1&&a[i+1]!=1) {
            cout<<"i: "<<i<<endl;
            a[i]=1;
            cnt++;
            i++;
        }
    }
    return cnt;
}
int main()
{
    freopen("in.txt","r",stdin);
    freopen("out.txt","w",stdout);
    for(int k=0;k<10;k++) {
        memset(a,-1,sizeof(a));
        cnt=0;
        cin>>n;
        for(int i=1;i<=n;i++) {
            cin>>a[i];
        }
        cout<<func(a)<<endl;
    }

    return 0;
}
```



### n个有序链表合并

```c++
#include <iostream>
using namespace std;
struct ListNode {
    int val;
    ListNode *next;
    ListNode() : val(0), next(nullptr) {}
    ListNode(int x) : val(x), next(nullptr) {}
    ListNode(int x, ListNode *next) : val(x), next(next) {}
};

ListNode* mergeTwoLists(ListNode* l1,ListNode* l2) {
    ListNode* root,* p1,* p2;
    ListNode* p=root;
    p1=l1->next;
    p2=l2->next;
    p=new ListNode;
    root=p;
    while(p1&&p2) {
        //cout<<l2->next->val<<endl;
        if(p1->val<p2->val) {
            p->next=p1;
            p=p->next;
            p1=p1->next;
        } else {
            p->next=p2;
            p=p->next;
            p2=p2->next;
        }
        
    }
    if(!p1) {
        p->next=p2;
        return root;
    }
    else {
        p->next=p1;
        return root;
    }
}

int main() {

    int n;
    cin>>n;
    ListNode* p[n];
    getchar();
    for(int i=0;i<n;i++) {
        int t;
        p[i]=new ListNode;
        ListNode* root;
        root=new ListNode;
        p[i]=root;
        while(1) {
            scanf("%d",&t);
            root->next=new ListNode(int(t));
            root=root->next;
            char c=getchar();
            if(c=='\n') break;
        }
    }
    for(int i=0;i<n-1;i++)
        p[i+1]=mergeTwoLists(p[i],p[i+1]);
    ListNode* root=p[n-1];
    root=root->next;
    while(root) {
        printf("%d ",root->val);
        root=root->next;
    }
    return 0;
}
```

