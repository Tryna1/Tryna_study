**题意：** 编写一个函数，输入是一个无符号整数（以二进制串的形式），返回其二进制表达式中数字位数为 '1' 的个数（也被称为 汉明重量).）。


**题解：** 使用与运算符和右移运算符计算1的数量。

```java
public class Solution {
    // you need to treat n as an unsigned value
    public int hammingWeight(int n) {
        int ans = 0;
        while(n != 0) {
            if((n & 1) == 1)
                ans++;
            n >>>= 1;
        }
        return ans;
    }
}
```