**题意：** 给定一个非负整数 n ，请计算 0 到 n 之间的每个数字的二进制表示中 1 的个数，并输出一个数组。


**题解：** $O(nlogn)$的解法很容易给出，这篇题解提供的是$O(n)$的解法。

我们设$dp[i]$ 为$i$的二进制中$1$的个数

* 当$i$为奇数时，他的个数比上一个偶数多1，多的就是最低位的$1$
* 当$i$为偶数时，他的最低位为$0$，所以他的个数等于整体右移一位

故
* dp[i] = dp[i - 1] + 1  i 为奇数
* dp[i] = dp[i / 2] i 为偶数

```java
class Solution {
    public int[] countBits(int n) {
        int[] dp = new int[n + 1];
        dp[0] = 0;
        for(int i = 1; i <= n; i++) {
            if(i % 2 == 1)
                dp[i] = dp[i - 1] + 1;
            else dp[i] = dp[i / 2];
        }
        return dp;
    }
}
```