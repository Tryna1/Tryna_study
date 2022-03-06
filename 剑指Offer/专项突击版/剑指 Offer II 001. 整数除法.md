**题意：** 给定两个整数 a 和 b ，求它们的除法的商 a/b ，要求不得使用乘号 '*'、除号 '/' 以及求余符号 '%' 。

**题解：** a / b = k 余 c， 枚举二进制位来找到这个k即可。 注意整数溢出的情况


```java
class Solution {
    public int divide(int a, int b) {
        if(a == Integer.MIN_VALUE && b == -1)
            return Integer.MAX_VALUE;
        int res = 0;
        int sign = (a > 0) ^ (b > 0) ? -1 : 1;
        a = Math.abs(a);
        b = Math.abs(b);
        for(int i = 31; i >= 0; i--) {
            if((a >>> i) - b >= 0) {
                a -= (b << i);
                res += (1 << i);
            }
        }
        return sign != -1 ? res : -res;
    }
}
```