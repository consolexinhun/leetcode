# 归并排序

{% hint style="info" %}
注意：这是左闭右开区间，\[left, right\]

所以merge函数，如果r = l+1，那么只有l一个元素，直接跳出
{% endhint %}

```cpp
class Solution {
public:
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     * 将给定数组排序
     * @param arr int整型vector 待排序的数组
     * @return int整型vector
     */
    vector<int> MySort(vector<int>& arr) {
        // write code here
        mergeSort(arr, 0, arr.size());
        return arr;
    }
    void mergeSort(vector<int>&arr, int l, int r){
        if(r-l < 2) return ;
        int mid = l + (r-l)/2;
        mergeSort(arr, l, mid);
        mergeSort(arr, mid, r);
        merge(arr, l, mid, r);
    }
    void merge(vector<int>&arr, int l, int mid, int r){
        //从l 到 r-1，一共r-l个元素
        int t[r-l];
        int k = 0;
        int i = l, j = mid;
        while(i < mid && j < r){
            if(arr[i] < arr[j]){
                t[k++] = arr[i++];
            }else{
                t[k++] = arr[j++];
            }
        }
        while(i < mid){
            t[k++] = arr[i++];
        }
        while(j < r){
            t[k++] = arr[j++];
        }
        
        for(int i = 0; i < r-l; i++){
            arr[l+i] = t[i];
        }
    }
};
```

