**题意：** 统计一个数字在排序数组中出现的次数。

**题解：** 直接顺序遍历即可，也可以采用二分，找到左右端点然后求区间长度。

```java
class Solution {
    public int search(int[] nums, int target) {
        int ans = 0;
        for(int i = 0; i < nums.length; i++) {
            if(nums[i] > target) break;
            if(nums[i] == target) ans++;
        }
        return ans;
    }
}
```