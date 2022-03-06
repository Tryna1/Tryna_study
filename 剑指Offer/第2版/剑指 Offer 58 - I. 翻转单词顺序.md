**题意：** 输入一个英文句子，翻转句子中单词的顺序，但单词内字符的顺序不变。为简单起见，标点符号和普通字母一样处理。例如输入字符串"I am a student. "，则输出"student. a am I"。

**题解：** 不使用库函数还是挺麻烦的。

* trim() 删除字符串开头和结尾的空格
* split() 以括号内的符号来分割字符串

```java
class Solution {
    public String reverseWords(String s) {
        String[] str = s.trim().split(" ");
        StringBuilder res = new StringBuilder();
        for(int i = str.length - 1; i >= 0; i--) {
            if(str[i].equals("")) continue;
            res.append(str[i] + " ");
        }
        return res.toString().trim();
    }
}
```