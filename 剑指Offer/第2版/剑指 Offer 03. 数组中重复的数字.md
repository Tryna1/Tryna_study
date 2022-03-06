**题意：** 在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

**题解：** 使用`HashMap`判重复出现即可

```java
class Solution {
    public int findRepeatNumber(int[] nums) {
        HashMap<Integer, Integer> mp = new HashMap<Integer, Integer>();
        for(int i = 0; i < nums.length; i++) {
            if(mp.containsKey(nums[i]))
                return nums[i];
            mp.put(nums[i], 1);
        }
        return 0;
    }
}
```