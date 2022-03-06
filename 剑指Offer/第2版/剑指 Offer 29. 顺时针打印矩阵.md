**题意：** 输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字。

**题解：** 模拟一下就好了，注意点细节。

```java
class Solution {

    int[][] moven = {{0, 1}, {1, 0}, {0, -1}, {-1, 0}};
    int num = 0;
    int[] ans;
    int[][] vis;

    public int[] spiralOrder(int[][] matrix) {
        if(matrix.length == 0) return new int[] {};
        int tot = matrix.length * matrix[0].length;
        ans = new int[tot];
        vis = new int[matrix.length][matrix[0].length];
        dfs(0, -1, matrix.length, matrix[0].length, 0, tot, matrix);
        return ans;
    }

    public boolean check(int x, int y, int n, int m) {
        if(x >= n || x < 0 || y >= m || y < 0 || vis[x][y] == 1) return false;
        return true;
    }

    public void dfs(int x, int y, int n, int m, int op, int tot, int[][] matrix) {
        if(num == tot) return;
        if(check(x + moven[op][0], y + moven[op][1], n, m) == true) {
            ans[num] = matrix[x + moven[op][0]][y + moven[op][1]];
            vis[x + moven[op][0]][y + moven[op][1]] = 1;
            num++;
            dfs(x + moven[op][0], y + moven[op][1], n, m, op, tot, matrix);
        }
        else {
            op = (op + 1) % 4;
            dfs(x, y, n, m, op, tot, matrix);
        } 
    }
}
```