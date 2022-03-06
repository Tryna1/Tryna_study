**题意：** 请定义一个队列并实现函数 max_value 得到队列里的最大值，要求函数max_value、push_back 和 pop_front 的均摊时间复杂度都是O(1)。

若队列为空，pop_front 和 max_value 需要返回 -1


**题解：** 写过了上一题这题就很简单了，维护一个双端单调队列即可。

**注意：** `Integer`直接的比较不能用`==`，应用`equals`

```java
class MaxQueue {

    Queue<Integer> q;
    Deque<Integer> dq;

    public MaxQueue() {
        q = new LinkedList<>();
        dq = new LinkedList<>();
    }
    
    public int max_value() {
        if(dq.isEmpty()) return -1;
        return dq.getFirst();
    }
    
    public void push_back(int value) {
        q.add(value);
        while(!dq.isEmpty() && dq.getLast() < value)
            dq.removeLast();
        dq.addLast(value);
    }
    
    public int pop_front() {
        if(q.isEmpty()) return -1;
        if(dq.getFirst().equals(q.element())) {
            dq.removeFirst();
        }
        return q.remove();
    }
}

/**
 * Your MaxQueue object will be instantiated and called as such:
 * MaxQueue obj = new MaxQueue();
 * int param_1 = obj.max_value();
 * obj.push_back(value);
 * int param_3 = obj.pop_front();
 */
```