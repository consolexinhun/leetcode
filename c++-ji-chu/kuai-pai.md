# 快排

> 核心就是找到一个基准，使得左边的元素都比它小，右边的元素都比它大
>
> partition函数：
>
> 先令base为第一个元素，high指针从右往左，找到第一个比base小的，换成low的值
>
> low指针从左往右，找到第一个比base大的，换成high的值
>
> low的值为base（因为之前记录的是high），返回low指针就行了

{% hint style="info" %}
注意：快排是左闭右闭区间，而归并是左闭右开区间
{% endhint %}

```cpp
class Solution {
public:
    vector<int> sortArray(vector<int>& nums) {
        quickSort(nums, 0, nums.size()-1);
        return nums;
    }

    int partition(vector<int>&v, int low, int high){
        int base = v[low];
        while(low < high){
            // 从右往左 找到第一个比base小的
            while(low < high && v[high] >= base){
                high--;
            }
            v[low] = v[high];
            //从左往右 找到第一个比base大的
            while(low < high && v[low] <= base){
                low ++;
            }
            v[high] = v[low];
        }
        v[low] = base;
        return low;
    }

    void quickSort(vector<int>&nums, int low, int high){
        if(low > high) return ;
        int privot = partition(nums, low, high);
        quickSort(nums, low, privot-1);
        quickSort(nums, privot+1, high);
    }
};
```

