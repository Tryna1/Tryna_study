**题意：** 给定一个数组 nums 和滑动窗口的大小 k，请找出所有滑动窗口里的最大值。

**题解：** 维护一个单调队列，因为首位都有删除操作，所以我们使用双端队列

* 当队首的值为滑动窗口中要删掉的值时，删掉队首元素
* 对于滑动窗口中新增的值，从队尾开始比较，如果队尾的值比新加入的值小就删除，否则就加入新元素。

```java
class Solution {
    public int[] maxSlidingWindow(int[] nums, int k) {
        int[] res = new int[nums.length - k + 1];
        if(nums.length == 0) return new int[] {};
        Deque<Integer> q = new LinkedList<>();
        for(int i = 0; i < k; i++) {
            while(!q.isEmpty() && q.getLast() < nums[i])
                q.removeLast();
            q.addLast(nums[i]);
        }
        res[0] = q.getFirst();
        for(int i = k; i < nums.length; i++) {
            if(q.getFirst() == nums[i - k])
                q.removeFirst();
            while(!q.isEmpty() && q.getLast() < nums[i])
                q.removeLast();
            q.addLast(nums[i]);
            res[i - k + 1] = q.getFirst();
        }
        return res;
    }
}
```