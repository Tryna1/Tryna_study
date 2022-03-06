**题意：** 从若干副扑克牌中随机抽 5 张牌，判断是不是一个顺子，即这5张牌是不是连续的。2～10为数字本身，A为1，J为11，Q为12，K为13，而大、小王为 0 ，可以看成任意数字。A 不能视为 14。

**题解：** 若能构成顺子，一定满足最大值和最小值的差不超过5，然后在判断除0以外有无数字重复出现即可。

```java
class Solution {
    public boolean isStraight(int[] nums) {
        HashMap<Integer, Integer> mp = new HashMap<Integer, Integer>();
        int minn = Integer.MAX_VALUE, maxx = Integer.MIN_VALUE;
        for(int num : nums) {
            if(num == 0) continue;
            maxx = Math.max(maxx, num);
            minn = Math.min(minn, num);
            if(mp.containsKey(num)) return false;
            mp.put(num, 1);
        }
        return maxx - minn < 5;
    }
}
```