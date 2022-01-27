**题意：** 输入一个非负整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。

**题解：** 对于两个字符串$x,y$，我们定义一种排序规则，如果$"x + y < y + x"$，那么就说明$x < y$，因为$x$放在左边更优。

```java
class Solution {
    public String minNumber(int[] nums) {
        String[] strs = new String[nums.length];
        for(int i = 0; i < nums.length; i++)
            strs[i] = String.valueOf(nums[i]);
        Arrays.sort(strs, (x, y) -> (x + y).compareTo(y + x));
        StringBuilder res = new StringBuilder();
        for(String str : strs)
            res.append(str);
        return res.toString();
    }
}
```