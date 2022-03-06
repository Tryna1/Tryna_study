**题意：** 我们把只包含质因子 2、3 和 5 的数称作丑数（Ugly Number）。求按从小到大的顺序的第 n 个丑数。


**题解：** 我们令$dp_i$为第$i + 1$个丑数，那么有三种转移$*2 、* 3$或者 $* 5$，然后使用三个指针记录一下从哪里转移过来。

```java
class Solution {
    public int nthUglyNumber(int n) {
        int[] dp = new int[n];
        int a = 0, b = 0, c = 0;
        dp[0] = 1;
        for(int i = 1; i < n; i++) {
            int p1 = dp[a] * 2, p2 = dp[b] * 3, p3 = dp[c] * 5;
            dp[i] = Math.min(Math.min(p1, p2), p3);
            if(p1 == dp[i]) a++;
            if(p2 == dp[i]) b++;
            if(p3 == dp[i]) c++;
        }
        return dp[n - 1];
    }
}
```