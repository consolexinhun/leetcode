# 二分

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


```

```cpp
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

