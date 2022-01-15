**题意：** 一个长度为n-1的递增排序数组中的所有数字都是唯一的，并且每个数字都在范围0～n-1之内。在范围0～n-1内的n个数字中有且只有一个数字不在该数组中，请找出这个数字。

**题解：** 因为都是$0$ ~ $n - 1$，并且是递增的，而且数字都是唯一的，所以正常情况下值应该与下标一致，不一致的话就输出，注意边界条件即可。


```java
class Solution {
    public int missingNumber(int[] nums) {
        for(int i = 0; i < nums.length; i++) {
            if(nums[i] != i) return i;
        }
        return nums.length;
    }
}
```