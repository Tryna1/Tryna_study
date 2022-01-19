**题意：** 一只青蛙一次可以跳上1级台阶，也可以跳上2级台阶。求该青蛙跳上一个 n 级的台阶总共有多少种跳法。

**题解：** 假设青蛙要跳到第$n$级台阶，那他可以从$n - 1$级台阶跳上来，也可以从$n - 2$级台阶跳上来。所以递推公式为$f_n = f_{n - 1} + f_{n - 2}$

```java
class Solution {
    int mod = 1000000007;
    public int numWays(int n) {
        int[] f = new int[n + 2];
        f[0] = 1;
        f[1] = 1;
        for(int i = 2; i <= n; i++)
            f[i] = (f[i - 1] + f[i - 2]) % mod;
        return f[n]; 
    }
}
```