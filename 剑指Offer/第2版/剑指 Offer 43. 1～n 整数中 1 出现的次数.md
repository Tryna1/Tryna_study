**题意：** 输入一个整数 n ，求1～n这n个整数的十进制表示中1出现的次数。

例如，输入12，1～12这些整数中包含1 的数字有1、10、11和12，1一共出现了5次。

**题解：** 可以数位dp做，当记录状态的时候要记录到当前这一位已经有多少个$1$了


```java
class Solution {

    int[][] dp = new int[20][20];
    int[] dig = new int[20];

    public int countDigitOne(int n) {
        for(int i = 0; i < 20; i++) 
            for(int j = 0; j < 20; j++)
                dp[i][j] = -1;
        int pos = 0;
        while(n != 0) {
            dig[pos++] = n % 10;
            n = n / 10;
        }
        return dfs(pos - 1, true, 0);
    }

    public int dfs(int pos, boolean limit, int num) {
        System.out.println(num);
        if(pos == -1) return num;
        if(!limit && dp[pos][num] != -1) return dp[pos][num];
        int up = limit ? dig[pos] : 9;
        int ans = 0;
        for(int i = 0; i <= up; i++) {
            ans += dfs(pos - 1, limit && (i == up), num + (i == 1 ? 1 : 0));
        }
        if(!limit) dp[pos][num] = ans;
        return ans;
    }

}
```