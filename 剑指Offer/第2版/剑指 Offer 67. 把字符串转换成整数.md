**题意：** 写一个函数 StrToInt，实现把字符串转换成整数这个功能。不能使用 atoi 或者其他类似的库函数。

**题解：** 按题意模拟即可


```java
class Solution {
    public int strToInt(String str) {
        str = str.trim();
        if(str.equals("")) return 0;
        int flag = 0;
        if(str.charAt(0) == '+')
            flag = 1;
        else if(str.charAt(0) == '-')
            flag = -1;
        else if(!check(str.charAt(0))) return 0;
        long x = 0;
        for(int i = Math.abs(flag); i < str.length(); i++) {
            x = Math.abs(x);
            if(check(str.charAt(i)))
                x = 10 * x + (str.charAt(i) - '0');
            else break;
            if(flag != 0) x *= flag;
            if(x > Integer.MAX_VALUE) 
                return Integer.MAX_VALUE;
            if(x < Integer.MIN_VALUE)
                return Integer.MIN_VALUE;
        }
        if(flag != 0) x = Math.abs(x) * flag;
        return (int)x;
    }

    public boolean check(char ch) {
        if(ch <= '9' && ch >= '0') return true;
        return false;
    }

}
```