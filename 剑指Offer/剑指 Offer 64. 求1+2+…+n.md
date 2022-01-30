**题意：** 求 1+2+...+n ，要求不能使用乘除法、for、while、if、else、switch、case等关键字及条件判断语句（A?B:C）。

**题解：** 可以递归也可以直接使用公式。

```java
class Solution {
    public int sumNums(int n) {
        if(n == 1) return 1;
        return sumNums(n - 1) + n;
    }
}
```