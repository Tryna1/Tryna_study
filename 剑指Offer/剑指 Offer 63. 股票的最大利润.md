**题意：** 假设把某股票的价格按照时间先后顺序存储在数组中，请问买卖该股票一次可能获得的最大利润是多少？

**题解：** 维护一个最小值即可

```java
class Solution {
    public int maxProfit(int[] prices) {
        int minn = Integer.MAX_VALUE;
        int ans = 0;
        for(int pri : prices) {
            minn = Math.min(minn, pri);
            ans = Math.max(ans, pri - minn);
        }
        return ans;
    }
}
```