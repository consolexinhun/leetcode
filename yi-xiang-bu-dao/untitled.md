# 1109.航班预定统计

差分数组：能够快速实现数组某个区间同时加上某个数或者减少某个数

差分数组构造：

```java
int[] diff = new int[nums.length];
// 构造差分数组
diff[0] = nums[0];
for (int i = 1; i < nums.length; i++) {
    diff[i] = nums[i] - nums[i - 1];
}
```

差分数组反推原数组：

```java
int[] res = new int[diff.length];
// 根据差分数组构造结果数组
res[0] = diff[0];
for (int i = 1; i < diff.length; i++) {
    res[i] = res[i - 1] + diff[i];
}
```

如果想对区间`nums[i..j]`的元素全部加3，只需要让`diff[i]+=3`，并且`diff[j+1] -= 3`，不过需要判断`j+1`是否超过数组边界。

```java
class Difference {
    // 差分数组
    private int[] diff;

    public Difference(int[] nums) {
        assert nums.length > 0;
        diff = new int[nums.length];
        // 构造差分数组
        diff[0] = nums[0];
        for (int i = 1; i < nums.length; i++) {
            diff[i] = nums[i] - nums[i - 1];
        }
    }

    /* 给闭区间 [i,j] 增加 val（可以是负数）*/
    public void increment(int i, int j, int val) {
        diff[i] += val;
        if (j + 1 < diff.length) {
            diff[j + 1] -= val;
        }
    }

    public int[] result() {
        int[] res = new int[diff.length];
        // 根据差分数组构造结果数组
        res[0] = diff[0];
        for (int i = 1; i < diff.length; i++) {
            res[i] = res[i - 1] + diff[i];
        }
        return res;
    }
}
```

LeetCode解法：

```cpp
#include<bits/stdc++.h>
using namespace std;

class Solution {
public:
    vector<int> corpFlightBookings(vector<vector<int>>& bookings, int n) {
        vector<int> res(n, 0);
        vector<int>diff(n, 0);
        for(int i = 0; i < bookings.size(); i++){
            int start = bookings[i][0];
            int end = bookings[i][1];
            int value = bookings[i][2];

            diff[start-1] += value;

            if (end < n){
                diff[end-1] -= value;
            }
        }
        res[0] = diff[0];
        for(int i = 1; i < n; i++){
            res[i] = res[i-1] + diff[i];
        }
        return res;
    }
};
int main(){
    Solution s;
    vector<vector<int>> v;
    v.push_back(vector<int>{1, 2, 10});
    v.push_back(vector<int>{2, 3, 20});
    v.push_back(vector<int>{2, 5, 25});
    s.corpFlightBookings(v, 5);
    return 0;
}
```

