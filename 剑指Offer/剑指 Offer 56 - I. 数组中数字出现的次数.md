**题意：** 一个整型数组 nums 里除两个数字之外，其他数字都出现了两次。请写程序找出这两个只出现一次的数字。要求时间复杂度是O(n)，空间复杂度是O(1)。

**题解：** 

* 我们设不同的两个数位$x,y$，将整个数组异或一遍，我们可以得到$x \oplus y$的值
* 遍历这个值的二进制位，找到第一个1出现的位置，因为这个位置上的$x,y$的情况必定不同。
* 根据这个位置上是否为1，将整个数组分成两个数组来处理，使得$x,y$不在同一个数组中。

```java
class Solution {
    public int[] singleNumbers(int[] nums) {
        int x = 0, y = 0, m = 1, n = 0;
        for(int num : nums)
            n ^= num;
        while((n & m) == 0)
            m <<= 1;
        for(int num : nums) {
            if((num & m) == 0) x ^= num;
            else y ^= num;
        }
        return new int[] {x, y};
    }
}
```