# 0509.斐波那契

{% hint style="info" %}
记忆化搜索
{% endhint %}

```cpp
#include<bits/stdc++.h>
using namespace std;

//0, 1, 1, 2, 3, 5, 8

vector<int> v(31, 0);

class Solution {
public:
    int fib(int N) {
        if (N == 0 ) return 0;
        if (N == 1) return 1;

        if (v[N] != 0){
            return v[N];
        }
        v[N] = fib(N-1) + fib(N-2);
        return v[N];
    }
};
int main(){
    v[1] = 1;

    Solution s;
    int t = s.fib(6);
    cout<<t;
    return 0;
}

/**  下面是提交的
 *
 */


/*
vector<int> v(30+1, 0);

class Solution {
public:
    int fib(int N) {
        v[1] = 1;
        return b(N);
    }

    int b(int N){
        if (N == 0) {
            return v[0];
        }
        if(N== 1){
            return v[1];
        }

        if(v[N] != 0){
            return v[N];
        }

        v[N] = b(N-1) + b(N-2);

        return v[N];
    }
};*/
```

{% page-ref page="../" %}

