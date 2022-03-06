**题解：** 数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。

**题意：** 采用正负相抵的形式，如果当前值为0的话，则当前值为假设的众数。

```java
class Solution {
    public int majorityElement(int[] nums) {
        int ans = 0, x = 0;
        for(int num : nums) {
            if(ans == 0) x = num;
            ans += num == x ? 1 : -1;
        }
        return x;
    }
}
```