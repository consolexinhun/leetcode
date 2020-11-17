# 0051.N皇后

```bash
路径：row(board)
选择列表：1 to n (第row行的所有列都是待选项)
结束条件：row从0开始，直到n结束
res = []
dfs(row, board):
    if row == n:
        res.add(board)
    for col = 0 to n-1:
        if (row, col, board)不合法：
            继续
        board[row][col] = Q
        dfs(row+1, board)
        board[row][col] = .
```

```cpp
#include<bits/stdc++.h>
using namespace std;
vector<vector<string>> res;
int len;
class Solution {
public:
    vector<vector<string>> solveNQueens(int n) {
        res.clear();
        len = n;

        vector<string> board(n, string(n, '.'));
        int row = 0;
        dfs(row, board);
        return res;
    }
    /**
     * 在board[row][col]放棋子是否和前row行的地区有冲突
     * @param row
     * @param col
     * @param board
     * @return 是否有效
     */
    bool isValid(int row, int col, vector<string>board){
        int n = board.size();
        for(int i = 0; i < row; i++){ //这一列
            if (board[i][col] == 'Q')
                return false;
        }
        for(int i = row-1, j=col+1; i>=0 && j<n; i--,j++){
            if(board[i][j] == 'Q')
                return false;
        }
        for(int i = row-1, j=col-1; i>=0 && j>=0; i--,j--){
            if (board[i][j] == 'Q')
                return false;
        }
        return true;
    }
    void dfs(int row, vector<string>board){
        if( row == len){
            res.push_back(board);
            return ;
        }

        for (int col = 0; col < len; col++){
            if (!isValid(row, col, board)){
                continue;
            }
            board[row][col] = 'Q';
            dfs(row+1, board);
            board[row][col] = '.';
        }
    }
};
int main(){
    Solution s;
    vector<vector<string>> res= s.solveNQueens(4);
    for(int i = 0; i < res.size(); i++){
        for(int j = 0; j < res[i].size(); j++){
            cout<<res[i][j]<<"   ";
            if (j == res[i].size()-1){
                cout<<endl;
            }
        }
    }
    return 0;
}
```

