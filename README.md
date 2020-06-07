# water-problems

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



