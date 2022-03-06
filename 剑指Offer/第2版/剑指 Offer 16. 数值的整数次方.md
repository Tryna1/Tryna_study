**题意：** 实现 pow(x, n) ，即计算 x 的 n 次幂函数（即，xn）。不得使用库函数，同时不需要考虑大数问题。

**题解：** 快速幂即可。

```java
class Solution {
    public double myPow(double x, int n) {
        double ans = 1;
        long k = n;
        if(k < 0) {
            k = -k;
            x = 1 / x;
        }
        while(k != 0) {
            if((k & 1) == 1)
                ans = ans * x;
            x = x * x;
            k >>= 1;
        }
        return ans;
    }
}
```