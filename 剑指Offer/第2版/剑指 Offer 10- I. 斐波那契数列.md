**题意：** 写一个函数，输入 n ，求斐波那契（Fibonacci）数列的第 n 项（即 F(N)）。

**题解：** 直接$O(n)$递推即可，当然也可以采用$O(log_n)$的矩阵快速幂。

```java
class Solution {
    int mod = 1000000007;
    public int fib(int n) {
        int[] f = new int[n + 2];
        f[1] = 1;
        for(int i = 2; i <= n; i++)
            f[i] = (f[i - 1] + f[i - 2]) % mod;
        return f[n]; 
    }
}
```

