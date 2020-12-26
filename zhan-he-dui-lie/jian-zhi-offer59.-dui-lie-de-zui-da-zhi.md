# 剑指Offer59.队列的最大值

单调递减队列

```cpp
class MaxQueue {
public:
    deque<int>d; // 单调递减队列

    deque<int>q; //普通队列
    
    MaxQueue() {
        
    }
    
    int max_value() {
        return d.empty() ? -1 : d.front();
    }
    
    void push_back(int value) {
        while(!d.empty() && value > d.back()){
            d.pop_back();
        }
        d.push_back(value);

        q.push_back(value);
    }
    
    int pop_front() {
        if(q.empty()) return -1;
        else if(q.front() == d.front()){ //如果要弹掉的就是最大的
            q.pop_front();
            int res = d.front();
            d.pop_front();
            return res;
        }else{  // 弹掉的肯定比最大的小
            int remp = q.front();
            q.pop_front();
            return remp;
        }
    }
};

/**
 * Your MaxQueue object will be instantiated and called as such:
 * MaxQueue* obj = new MaxQueue();
 * int param_1 = obj->max_value();
 * obj->push_back(value);
 * int param_3 = obj->pop_front();
 */
```

