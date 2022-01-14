**题意：** 字符串的左旋转操作是把字符串前面的若干个字符转移到字符串的尾部。请定义一个函数实现字符串左旋转操作的功能。比如，输入字符串"abcdefg"和数字2，该函数将返回左旋转两位得到的结果"cdefgab"。

**题解：** 题目很简单，但为了追求效率，尽量不要再循环里面写字符串的`+=`吧， 第一种方法54ms，第二种方法0ms，效率区别还是挺大的。


```java
class Solution {
    public String reverseLeftWords(String s, int n) {
        String s1 = "";
        for(int i = n; i < s.length(); i++) {
            s1 += s.charAt(i);
        }
        for(int i = 0; i < n; i++) {
            s1 += s.charAt(i);
        }
        return s1;
    }
}
```


```java
class Solution {
    public String reverseLeftWords(String s, int n) {
        return s.substring(n, s.length()) + s.substring(0, n);
    }
}
```