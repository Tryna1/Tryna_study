**题意：** 输入一个递增排序的数组和一个数字s，在数组中查找两个数，使得它们的和正好是s。如果有多对数字的和等于s，则输出任意一对即可。

**题解：** 利用两个指针，一个记录左端点，一个记录右端点，因为数组是递增的，所以比较这两个值得和，在考虑将指针进行对应的移动。

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int p1 = 0, p2 = nums.length - 1;
        while(nums[p1] + nums[p2] != target) {
            if(nums[p1] + nums[p2] < target)
                p1++;
            else p2--;
        }
        return new int[] {nums[p1], nums[p2]};
    }
}
```