**题意：** 输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有奇数在数组的前半部分，所有偶数在数组的后半部分。

**题解：** 使用双指针，一个从前往后，一个从后往前。

```java
class Solution {
    public int[] exchange(int[] nums) {
        int[] res = new int[nums.length];
        int p1 = 0, p2 = nums.length - 1;
        for(int i = 0; i < nums.length; i++) {
            if(nums[i] % 2 == 1) {
                res[p1++] = nums[i];
            }
            else res[p2--] = nums[i];
        }
        return res;
    }
}
```