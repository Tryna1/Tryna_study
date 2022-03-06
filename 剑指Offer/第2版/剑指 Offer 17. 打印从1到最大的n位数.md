**题意：** 输入数字 n，按顺序打印出从 1 到最大的 n 位十进制数。比如输入 3，则打印出 1、2、3 一直到最大的 3 位数 999。

**题解：** 直接模拟就行，数据范围大的话需要用字符串模拟。

```java
class Solution {
    public int[] printNumbers(int n) {
        int up = (int)Math.pow(10, n) - 1;
        int[] res = new int[up];
        for(int i = 0; i < up; i++)
            res[i] = i + 1;
        return res;
    }
}
```