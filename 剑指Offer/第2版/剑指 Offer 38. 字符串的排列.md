**题意：** 输入一个字符串，打印出该字符串中字符的所有排列。

 

你可以以任意顺序返回这个字符串数组，但里面不能有重复元素。

**题解：** 通过dfs回溯来解决，中间用set来去重

```java
class Solution {

    HashSet<String> res = new HashSet<>();
    int[] vis;
    char[] val;
    public String[] permutation(String s) {
        val = s.toCharArray();
        vis = new int[val.length];
        dfs("", 0, val.length);
        String[] ans = new String[res.size()];
        int idx = 0;
        for(String str : res)
            ans[idx++] = str;
        return ans;
    }

    public void dfs(String tmp, int dep, int n) {
        if(dep == n) {
            res.add(tmp);
            return ;
        }
        for(int i = 0; i < n; i++) {
            if(vis[i] == 0) {
                vis[i] = 1;
                dfs(tmp + String.valueOf(val[i]), dep + 1, n);
                vis[i] = 0;    
            }
        }
    }
}
```