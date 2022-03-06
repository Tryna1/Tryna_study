**题意：** 如何得到一个数据流中的中位数？如果从数据流中读出奇数个数值，那么中位数就是所有数值排序之后位于中间的数值。如果从数据流中读出偶数个数值，那么中位数就是所有数值排序之后中间两个数的平均值。


**题解：**
* 使用两个堆来维护，一个是大顶堆，一个是小顶堆
* 大顶堆存放较小的部分，小顶堆存放较大的部分，这样中位数就可以用两个堆的顶部元素来计算。
* 如何保证较小的在大顶堆中，较大的在小顶堆中？
* 如果我需要向大顶堆中添加元素，首先将这个元素添加到小顶堆中，然后再弹出小顶堆的顶部元素来放入大顶堆中。保证每次加入大顶堆的都是最小的元素，反之向小顶堆中添加元素同理。

```java
class MedianFinder {

    Queue<Integer> A, B;

    /** initialize your data structure here. */
    public MedianFinder() {
        A = new PriorityQueue<>();
        B = new PriorityQueue<>((x, y) -> (y - x));
    }
    
    public void addNum(int num) {
        if(A.size() != B.size()) {
            A.add(num);
            B.add(A.remove());
        }
        else {
            B.add(num);
            A.add(B.remove());
        }
    }
    
    public double findMedian() {
        if(A.size() == B.size())
            return (A.element() + B.element()) / 2.0;
        return A.element();
    }
}

/**
 * Your MedianFinder object will be instantiated and called as such:
 * MedianFinder obj = new MedianFinder();
 * obj.addNum(num);
 * double param_2 = obj.findMedian();
 */
```