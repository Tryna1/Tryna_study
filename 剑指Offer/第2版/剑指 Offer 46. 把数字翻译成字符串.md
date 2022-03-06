**题意：** 给定一个数字，我们按照如下规则把它翻译为字符串：0 翻译成 “a” ，1 翻译成 “b”，……，11 翻译成 “l”，……，25 翻译成 “z”。一个数字可能有多个翻译。请编程实现一个函数，用来计算一个数字有多少种不同的翻译方法。

**题解：** 我们设$dp[i]$ 为以$i$结尾的方案数，我们考虑转移。

* 如果$x_{i}$和$x_{i - 1}$能一起翻译，也就是说$10 * x_{i-1} + x_i \leq 25$，分为两种情况，一起翻译和不一起翻译，所以$dp[i] = dp[i - 1] + dp[i - 2]$
* 如果不能一起翻译，那就只能单独翻译了，所以$dp[i] = dp[i - 1]$


```java
class Solution {
    public int translateNum(int num) {
        String s = Integer.toString(num);
        int[] dp = new int[s.length() + 1];
        dp[0] = 1;
        for(int i = 1; i < s.length(); i++) {
            if(check(s.charAt(i - 1), s.charAt(i)))
                dp[i] = dp[i - 1] + (i >= 2 ? dp[i - 2] : dp[i - 1]);
            else dp[i] = dp[i - 1];
        }
        return dp[s.length() - 1];
    }

    public boolean check(char i, char j) {
        if((i == '1' && j <= '9') || (i == '2' && j <= '5')) return true;
        return false;
    }
}
```