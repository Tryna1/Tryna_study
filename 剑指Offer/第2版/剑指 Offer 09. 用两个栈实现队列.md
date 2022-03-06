**题意：** 用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )

**题解：** 说实话刚开始刷这个连样例都看不懂，然后看了评论区的解释才能理解。就是用两个栈来模拟队列，但我第一版写的时间复杂度较差，其实没必要把第二个栈里的元素再放进原来的栈中。

**第一版**
```java
class CQueue {

    Stack<Integer> a, b;

    public CQueue() {
        a = new Stack<Integer>();
        b = new Stack<Integer>();
    }

    public void appendTail(int value) {
        a.push(value);
    }

    public int deleteHead() {
        if(a.empty())
            return -1;
        while(!a.empty()) {
            b.push(a.pop());
        }
        int tmp = b.pop();
        while(!b.empty()) {
            a.push(b.pop());
        }
        return tmp;
    }
}
```

**第二版：**
```java
class CQueue {

    Stack<Integer> a, b;

    public CQueue() {
        a = new Stack<Integer>();
        b = new Stack<Integer>();
    }

    public void appendTail(int value) {
        a.push(value);
    }

    public int deleteHead() {
        if(a.empty() && b.empty())
            return -1;
        if(b.empty()) {
            while(!a.empty())
                b.push(a.pop());
        }
        return b.pop();
    }
}
```
