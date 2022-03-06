**题意：** 输入一个整型数组，数组中的一个或连续多个整数组成一个子数组。求所有子数组的和的最大值。

**题解：** 设$dp[i]$ 为以$nums[i]$ 为结尾的子数组的和的最大值，所以转移有。
* $dp[i - 1] \leq 0$ 时 $dp[i] = nums[i]$
* $dp[i - 1] > 0$ 时 $dp[i] = dp[i - 1] + nums[i]$

```java
class Solution {
    public int maxSubArray(int[] nums) {
        int ans = nums[0];
        for(int i = 1; i < nums.length; i++) {
            if(nums[i - 1] > 0)
                nums[i] = nums[i - 1] + nums[i];
            ans = Math.max(ans, nums[i]);
        }
        return ans;
    }
}
```