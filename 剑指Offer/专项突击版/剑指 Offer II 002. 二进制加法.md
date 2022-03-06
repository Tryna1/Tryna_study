**题意：** 给定两个 01 字符串 a 和 b ，请计算它们的和，并以二进制字符串的形式输出。

**题解：** 二进制模拟一下就好了

```java
class Solution {
    public String addBinary(String a, String b) {
        if(a.equals("0") && b.equals("0"))
            return new String("0");
        StringBuilder str = new StringBuilder();
        int add = 0;
        int i = a.length() - 1;
        int j = b.length() - 1;
        while(i >= 0 || j >= 0) {
            int tmp = add;
            if(i >= 0)
                tmp += a.charAt(i--) - '0';
            if(j >= 0)
                tmp += b.charAt(j--) - '0';
            
            add = tmp / 2;
            str.append(tmp % 2);
        }
        if(add != 0) str.append('1');
        return str.reverse().toString();
    }
}
```