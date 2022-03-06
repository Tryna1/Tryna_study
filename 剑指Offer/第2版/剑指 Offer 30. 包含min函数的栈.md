**题意：** 定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)。

**题解：** 搞一个辅助栈，当插入的元素比这个栈头元素小时，我就更新插入栈的元素，类似单调栈的思想。最后一个辅助栈是一个从栈底向栈顶单调递增的栈。

```java
class MinStack {

    Stack<Integer> a;
    Stack<Integer> minn;
    /** initialize your data structure here. */
    public MinStack() {
        a = new Stack<Integer>();
        minn = new Stack<Integer>();
    }

    public void push(int x) {
        a.push(x);
        if(minn.empty()) minn.push(x);
        else {
            if(minn.peek() > x) minn.push(x); 
            else minn.push(minn.peek());  
        }
    }

    public void pop() {
        a.pop();
        minn.pop();
    }

    public int top() {
        return a.peek();
    }

    public int min() {
        return minn.peek();
    }
}

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(x);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.min();
 */
```