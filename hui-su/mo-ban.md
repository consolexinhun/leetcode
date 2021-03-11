# 模板

```text
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

