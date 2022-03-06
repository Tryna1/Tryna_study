**题意：** 给你一根长度为 n 的绳子，请把绳子剪成整数长度的 m 段（m、n都是整数，n>1并且m>1），每段绳子的长度记为 k[0],k[1]...k[m - 1] 。请问 k[0]*k[1]*...*k[m - 1] 可能的最大乘积是多少？例如，当绳子的长度是8时，我们把它剪成长度分别为2、3、3的三段，此时得到的最大乘积是18。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

**题解：** 和I的区别就是题目数据范围大了，这里利用了快速幂，然后注意乘法过程中会爆int的范围


```java
class Solution {

    int mod = 1000000007;

    public int cuttingRope(int n) {
        if(n <= 3) return n - 1;
        else if(n % 3 == 1) return (int)(qpow(3, n / 3 - 1) * (long)4 % mod);
        else if(n % 3 == 2) return qpow(3, n / 3) * 2 % mod;
        else return qpow(3, n / 3);
    }

    public int qpow(long n, int k) {
        long ans = 1;
        while(k > 0) {
            if((k & 1) == 1)
                ans = ans * n % mod;
            n = n * n % mod;
            k >>= 1;
        }
        return (int)ans;
    }

}
```