**题意：** 给你一根长度为 n 的绳子，请把绳子剪成整数长度的 m 段（m、n都是整数，n>1并且m>1），每段绳子的长度记为 k[0],k[1]...k[m-1] 。请问 k[0]*k[1]*...*k[m-1] 可能的最大乘积是多少？例如，当绳子的长度是8时，我们把它剪成长度分别为2、3、3的三段，此时得到的最大乘积是18。

**题解：** 当把每段绳子的长度分为3时，结果最优。

```java
class Solution {
    public int cuttingRope(int n) {
        if(n == 2) return 1;
        if(n == 3) return 2;
        int ans = (int) Math.pow(3, n / 3);
        if(n % 3 == 2) ans *= 2;
        else if(n % 3 == 1) ans = ans / 3 * 4;
        return ans;
    }
}
```