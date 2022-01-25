**题意：** 给定一个 `m x n` 二维字符网格 `board` 和一个字符串单词 `word` 。如果 `word` 存在于网格中，返回 `true` ；否则，返回 `false` 。

**题解：** 很常规的dfs，注意边界和终止条件，还有注意不能走回头路，回溯的时候记得把字符修改回去。

```java
class Solution {
    
    int[][] moven = {{1, 0}, {-1, 0}, {0, 1}, {0, -1}};
    
    public boolean exist(char[][] board, String word) {
        int n = board.length;
        int m = board[0].length;
        for(int i = 0; i < n; i++) {
            for(int j = 0; j < m; j++) {
                if(dfs(i, j, 0, n, m, board, word)) return true;
            }
        }
        return false;
    }

    public boolean dfs(int x, int y, int k, int n, int m, char[][] board, String word) {
        if(x < 0 || x >= n || y < 0 || y >= m || board[x][y] != word.charAt(k)) return false;
        if(k == word.length() - 1) return true;
        boolean res = false;
        char tmp = board[x][y];
        board[x][y] = '#';
        for(int i = 0; i < 4; i++) {
            res = (res || dfs(x + moven[i][0], y + moven[i][1], k + 1, n, m, board, word));
        }
        board[x][y] = tmp;
        return res;
    }
}
```

