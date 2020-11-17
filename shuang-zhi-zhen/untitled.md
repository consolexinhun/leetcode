# 0349.两个数组的交集

方法一：

二分

先将数组1排好序，然后遍历数组2，在数组1中二分查找数组2的元素

```cpp
#include<bits/stdc++.h>
using namespace std;


class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
        set<int> s;
        vector<int> res;

        sort(nums1.begin(), nums1.end());
        for(int i = 0; i < nums2.size(); i++){
            if(binary_search(nums1.begin(), nums1.end(), nums2[i])){
                s.insert(nums2[i]);
            }
        }

        for(auto it = s.begin(); it != s.end(); it++){ // set<int>iterator::it = s.begin()
            res.push_back(*it);
        }
        return res;
    }
};
int main(){
    Solution s;
    vector<int> num1 = {1, 2, 2, 1};
    vector<int> num2 = {2, 2};
    vector<int> res= s.intersection(num1, num2);
    return 0;
}
```

方法二：

双指针

先将两个数组都排好序，i指向数组1，j指向数组2，如果a\[i\] == b\[j\]，加到结果，i++,j++ 如果a\[i\] &lt; b\[j\], i++，否则j++

```cpp
#include<bits/stdc++.h>
using namespace std;


class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
        set<int> s;
        vector<int> res;

        sort(nums1.begin(), nums1.end());
        sort(nums2.begin(), nums2.end());

        int i = 0, j = 0;
        while(i != nums1.size() && j != nums2.size()){
            if(nums1[i] == nums2[j]){
                s.insert(nums2[j]);
                i++;
                j++;
            }
            else if(nums1[i] < nums2[j]){
                i++;
            }
            else if(nums1[i] > nums2[j]){
                j++;
            }
        }

        for(auto it = s.begin(); it != s.end(); it++){
            res.push_back(*it);
        }
        return res;
    }
};
int main(){
    Solution s;
    vector<int> num1 = {1, 2, 2, 1};
    vector<int> num2 = {2, 2};
    vector<int> res= s.intersection(num1, num2);
    return 0;
}
```

