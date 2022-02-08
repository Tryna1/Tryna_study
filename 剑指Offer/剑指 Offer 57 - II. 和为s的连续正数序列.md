**题意：** 输入一个正整数 target ，输出所有和为 target 的连续正整数序列（至少含有两个数）。

**题解：** 利用滑动窗口解决这题，当左区间大于等于右区间时退出，否则就将符合条件的窗口加入答案。

```java
class Solution {
    public int[][] findContinuousSequence(int target) {
        int i = 1, j = 2, sum = 3;
        List<int[]> ans = new LinkedList<>();
        while(i < j) {
            if(sum == target) {
                int[] tmp = new int[j - i + 1];
                for(int k = i; k <= j; k++)
                    tmp[k - i] = k;
                ans.add(tmp);
            }
            if(sum >= target) {
                sum -= i;
                i++;
            }
            else{
                j++;
                sum += j;
            }
        }
        return ans.toArray(new int[ans.size()][]);
    }
}
```