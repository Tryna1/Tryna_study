**题意：** 请从字符串中找出一个最长的不包含重复字符的子字符串，计算该最长子字符串的长度。

**题解：** 采用滑动窗口的方法来解决，我们遍历这个字符串，当当前这个字符在之前出现过得时候，我们就找到他之前出现的位置，记录为左端点，并且和之前的左端点取最大值，当前的位置到左端点就是合法的长度。


```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        HashMap<Character, Integer> mp = new HashMap<Character, Integer>();
        int left = -1;
        int ans = 0;
        for(int i = 0; i < s.length(); i++) {
            if(mp.containsKey(s.charAt(i))) {
                left = Math.max(left, mp.get(s.charAt(i)));
            }
            mp.put(s.charAt(i), i);
            ans = Math.max(ans, i - left);
        }
        return ans;
    }
}
```