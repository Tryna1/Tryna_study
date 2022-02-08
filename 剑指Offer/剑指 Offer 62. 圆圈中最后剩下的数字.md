**题意：** 0,1,···,n-1这n个数字排成一个圆圈，从数字0开始，每次从这个圆圈里删除第m个数字（删除后从下一个数字开始计数）。求出这个圆圈里剩下的最后一个数字。


**题解：** 经典的约瑟夫环问题，利用动态规划解决。

```java
class Solution {
    public int lastRemaining(int n, int m) {
        int x = 0;
        for(int i = 2; i <= n; i++) {
            x = (x + m) % i;
        }
        return x;
    }
}
```