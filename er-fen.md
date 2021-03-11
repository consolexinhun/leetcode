# 二分

> 两端闭写法
>
> 注意结束条件是 left = right + 1

```cpp
#include<bits/stdc++.h>
using namespace std;

// 两端闭
// 条件 left  = right + 1
int mylow_bound(vector<int>&v, int target){
    int l = 0, r = (int)v.size()-1;
    while(l <= r){
        int mid = l + (r-l)/2;
        if(v[mid] < target){
            l = mid+1;
        }
        else if(v[mid] == target){
            r = mid - 1;
        }else if(v[mid] > target){
            r = mid - 1;
        }
    }
    if(l == v.size() || v[l] != target) return -1;
    return l;
}

int myup_bound(vector<int>&v, int target){
    int l = 0, r = (int)v.size()-1;
    while(l <= r){
        int mid = l + (r-l)/2;
        if(v[mid] < target) {
            l = mid+1;
        }
        else if (v[mid] == target){
            l = mid+1;
        }else if(v[mid] > target){
            r = mid-1;
        }
    }
    if(r == -1 || v[r] != target) return -1;
    return r;
}



int main(){
    vector<int> s = {1, 2, 4, 4, 4, 5};
//    cout<<mylow_bound(s, 0)<<endl;
//    cout<<mylow_bound(s, 4)<<endl;
//    cout<<mylow_bound(s, 3)<<endl;
//    cout<<mylow_bound(s, 6)<<endl;
    cout<<myup_bound(s, 0)<<endl;
    cout<<myup_bound(s, 4)<<endl;
    cout<<myup_bound(s, 3)<<endl;
    cout<<myup_bound(s, 6)<<endl;
    return 0;
}

```

> 左闭右开写法



> 1、找到左边第一个等于target的值（返回left）
>
> 2、找到右边第一个等于target的值（返回right-1，因为相等的时候为mid+1）
>
> 由于结束条件是 left == right
>
> 注意相等的时候要压缩边界

```cpp
int mylow_bound(vector<int>&v, int t){
    int l = 0, r = v.size();
    while(l < r){
        int mid = l + (r-l)/2;
        if(v[mid] < t){
            l = mid+1;
        }
        else if(v[mid] == t){
            r = mid;
        }else if(v[mid] > t){
            r = mid;
        }
    }

    if(l == v.size() || v[l] != t) return -1;
    return l;
}


int myup_bound(vector<int> &v, int t){
    int l = 0, r = v.size();
    while(l < r){
        int mid = l + (r-l)/2;
        if(v[mid] < t){
            l = mid+1;
        }
        else if(v[mid] == t){
            l = mid+1;
        }else if(v[mid] > t){
            r = mid;
        }
    }
    if(r == 0 || v[r-1] != t) return -1;
    return r-1;
}
```

