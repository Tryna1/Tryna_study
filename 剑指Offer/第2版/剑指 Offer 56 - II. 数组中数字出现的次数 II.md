**题意：** 在一个数组 nums 中除一个数字只出现一次之外，其他数字都出现了三次。请找出那个只出现一次的数字。

**题解：** 计算每一位二进制位上出现的次数，对于每一位的数量模3就是我们要找的那个数。


```java
class Solution {
    public int singleNumber(int[] nums) {
        int[] bit = new int[32];
        for(int num : nums) {
            for(int i = 0; i <= 31; i++) {
                if(((num >> i) & 1) == 1)
                    bit[i]++;
            }
        }
        int ans = 0, x = 1;
        for(int i = 0; i <= 31; i++) {
            if(bit[i] % 3 != 0)
                ans += x;
            x = x * 2;
        }
        return ans;
    }
}
```