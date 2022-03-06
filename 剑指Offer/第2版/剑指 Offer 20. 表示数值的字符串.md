**题意：** 请实现一个函数用来判断字符串是否表示数值（包括整数和小数）。

数值（按顺序）可以分成以下几个部分：

    1.若干空格
    2.一个 小数 或者 整数
    3.（可选）一个 'e' 或 'E' ，后面跟着一个 整数
    4.若干空格
小数（按顺序）可以分成以下几个部分：

    1.（可选）一个符号字符（'+' 或 '-'）
    2.下述格式之一：
        1.至少一位数字，后面跟着一个点 '.'
        2.至少一位数字，后面跟着一个点 '.' ，后面再跟着至少一位数字
        3.一个点 '.' ，后面跟着至少一位数字
整数（按顺序）可以分成以下几个部分：

    1.（可选）一个符号字符（'+' 或 '-'）
    2.至少一位数字
部分数值列举如下：

["+100", "5e2", "-123", "3.1416", "-1E-16", "0123"]
部分非数值列举如下：

["12e", "1a3.14", "1.2.3", "+-5", "12e+5.4"]

**题解：** 首先用`trim()`函数将首位的空格去掉，然后以`.`和`e || E` 当做分隔符将字符串分为三部分，然后写一个判断整数的函数，再加上是否能为空，是否能有符号的标记即可。

```java
class Solution {
    public boolean isNumber(String s) {
        s = s.trim();
        int num1 = -1, num2 = -1;
        for(int i = 0; i < s.length(); i++) {
            if(s.charAt(i) == '.') {
                if(num1 == -1) num1 = i;
                else return false;
            }
            if(s.charAt(i) == 'e' || s.charAt(i) == 'E') {
                if(num2 == -1) num2 = i;
                else return false;
            }
        }
        boolean f = true;
        if(num1 != -1) {
            int n = s.length() - 1;
            if(num1 == 0 && num1 == n) return false;
            else if(num1 == 0 && num1 != n) f = s.charAt(num1 + 1) <= '9' && s.charAt(num1 + 1) >= '0';
            else if(num1 != 0 && num1 == n) f = s.charAt(num1 - 1) <= '9' && s.charAt(num1 - 1) >= '0';
            else f = (s.charAt(num1 + 1) <= '9' && s.charAt(num1 + 1) >= '0') || (s.charAt(num1 - 1) <= '9' && s.charAt(num1 - 1) >= '0');
        }
        if(f == false) return false;
        if(num1 == -1 && num2 == -1) return check(s, 1, 0);
        else if(num1 == -1 && num2 != -1) return check(s.substring(0, num2), 1, 0) && check(s.substring(num2 + 1, s.length()), 1, 0);
        else if(num1 != -1 && num2 == -1) return check(s.substring(0, num1), 1, 1) && check(s.substring(num1 + 1, s.length()), 0, 1);
        else return check(s.substring(0, num1), 1, 1) && check(s.substring(num1 + 1, num2), 0, 1) && check(s.substring(num2 + 1, s.length()), 1, 0);
    }

    public boolean check(String s, int op, int len) {
        int p = 0;
        if(len == 0 && s.length() == p) return false;
        if(s.length() == 0) return true;        
        if(op == 1 && (s.charAt(p) == '-' || s.charAt(p) == '+'))
            p++;
        if(len == 0 && s.length() == p) return false;
        for(int i = p; i < s.length(); i++) {
            if(s.charAt(i) <= '9' && s.charAt(i) >= '0') continue;
            return false;
        }
        return true;
    }
}
```
