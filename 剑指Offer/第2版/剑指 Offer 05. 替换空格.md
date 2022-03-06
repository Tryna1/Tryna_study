**题意：** 请实现一个函数，把字符串 s 中的每个空格替换成"%20"。

**题解：** 简单题，遍历一遍就行了


```java
class Solution {
    public String replaceSpace(String s) {
        String ans = "";
        for(int i = 0; i < s.length(); i++) {
            if(s.charAt(i) == ' ')
                ans += "%20";
            else ans += s.charAt(i);
        }
        return ans;
    }
}

```