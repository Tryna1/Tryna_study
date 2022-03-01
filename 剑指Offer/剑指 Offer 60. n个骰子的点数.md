**题意：** 把n个骰子扔在地上，所有骰子朝上一面的点数之和为s。输入n，打印出s的所有可能的值出现的概率。

**题解：** 设$dp[n][m]$为有$n$个骰子并且和为$m$的概率，考虑转移，当加入一个新的骰子时，骰子点数可能是1，就从$m - 1$转移而来....

故转移方程为$$dp[n][m] = \sum_{i = 1}^{6}dp[n-1][m-i]*\frac{1}{6}$$

```java
class Solution {
    public double[] dicesProbability(int n) {
        double[][] dp = new double[n + 1][6 * n + 1];
        for(int i = 1; i <= 6; i++)
            dp[1][i] = 1 / 6.0;
        for(int i = 2; i <= n; i++) {
            for(int j = i; j <= 6 * i; j++) {
                for(int k = 1; k <= 6 && j - k > 0; k++) {
                    dp[i][j] += dp[i - 1][j - k] * (1 / 6.0);
                }
            }
        }
        double[] res = new double[5 * n + 1];
        for(int i = n; i <= 6 * n; i++)
            res[i - n] = dp[n][i];
        return res;
    }
}
```