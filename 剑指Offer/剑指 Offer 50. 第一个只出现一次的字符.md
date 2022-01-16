**题意：** 在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母。

**题解：** 用哈希表来记录单个字符出现的次数即可。碰见第一个次数为一次的输出。


```java
class Solution {
    public char firstUniqChar(String s) {
        HashMap<Character, Boolean> mp = new HashMap<Character, Boolean>();
        char[] sc = s.toCharArray();
        for(char c : sc) {
            if(mp.containsKey(c))
                mp.put(c, true);
            else
                mp.put(c, false);
        }
        for(char c : sc) {
            if(mp.get(c) == false)
                return c;
        }
        return ' ';
    }
}
```