**题意：** 数字以0123456789101112131415…的格式序列化到一个字符序列中。在这个序列中，第5位（从下标0开始计数）是5，第13位是1，第19位是4，等等。

请写一个函数，求任意第n位对应的数字。


**题解：** 可以分三步来进行

* 通过要求的数位确定是几位数
* 确定是这这个位数的第几个数字
* 确定这个数字中的第几个数字

**注意：** 计算过程中注意乘法会爆int的范围

```java
class Solution {
    public int findNthDigit(int n) {
        if(n == 0) return 0;
        long dig = 1;
        long sum = 9;
        long start = 1;
        while(true) {
            if(n - sum <= 0) {
                break;
            }
            System.out.println(dig * start * 9);
            n -= dig * start * 9;
            dig++;
            start *= 10;
            sum += dig * start * 9; 
        }
        long pos = (n - 1) / dig;
        long num = start + pos;
        pos = (n - 1) % dig;
        String str = String.valueOf(num);
        return str.charAt((int)pos) - '0';
    }
}
```