---
description: 回溯
---

# 0046.全排列

回溯算法框架

```cpp
result = [];
void dfs(路径，选择列表){
    if (满足条件){
        result.append(路径);
        return ;
    }

    for 选择 in 选择列表：
        做选择
        dfs(新路径，新选择列表)
        撤销选择

}
```

```cpp
vector<vector<int>> res ;

int len;

class Solution {
public:
    vector<vector<int>> permute(vector<int>& nums) {
        res.clear();
        vector<int> track;
        vector<int> choice;
        for(int i = 0; i < nums.size(); i++){
            choice.push_back(nums[i]);
        }
        len = nums.size();

        dfs(track, choice);
        return res;
    }

    void dfs(vector<int> track, vector<int>choice){
        if (track.size() == len){
            vector<int> temp(track);  //temp记录track所有内容
            res.push_back(temp);
            return ;
        }

        for(int i = 0; i < choice.size(); i++){
            track.push_back(choice[i]);

            vector<int>new_choice;
            for(int j = 0; j < choice.size(); j++){
                if (j != i){
                    new_choice.push_back(choice[j]);
                }
            }

            dfs(track, new_choice);
            track.pop_back();
        }
    }
};
```

或者

```cpp
#include<bits/stdc++.h>
using namespace std;
vector<vector<int>> res ;
int len;
class Solution {
public:
    vector<vector<int>> permute(vector<int>& nums) {
        res.clear();
        vector<int> track;
        len = nums.size();
        dfs(track, nums);
        return res;
    }
    void dfs(vector<int> track, vector<int>nums){
        /*
         * 递归终止条件
         */
        if (track.size() == len){
            vector<int> temp(track);  //temp记录track所有内容
            res.push_back(temp);
            return ;
        }

        for(int i = 0; i < nums.size(); i++){
            /**
             * 如果track中包含了nums[i]，那么直接下一步
             */
            bool flag = true;
            for(int j = 0; j < track.size(); j++){
                if (track[j] == nums[i]){
                    flag = false;
                    break;
                }
            }
            if (!flag){
                continue;
            }

            track.push_back(nums[i]);
            dfs(track, nums);
            track.pop_back();
        }
    }
};
int main(){
    Solution s;
    vector<int> nums = {1, 2, 3};
    s.permute(nums);

    for(int i = 0; i < res.size(); i ++){
        for(int j = 0; j < res[i].size(); j++){
            printf("%d%c", res[i][j], j==(res[i].size()-1) ? '\n' : ' ');
        }
    }
    return 0;
}
```

