**题意：** 地上有一个m行n列的方格，从坐标 [0,0] 到坐标 [m-1,n-1] 。一个机器人从坐标 [0, 0] 的格子开始移动，它每次可以向左、右、上、下移动一格（不能移动到方格外），也不能进入行坐标和列坐标的数位之和大于k的格子。例如，当k为18时，机器人能够进入方格 [35, 37] ，因为3+5+3+7=18。但它不能进入方格 [35, 38]，因为3+5+3+8=19。请问该机器人能够到达多少个格子？


**题解：** 很直白的搜索，用dfs或bfs都能做，我两个版本都实现一下好了。


**dfs：**

```java
class Solution {
    

    public int movingCount(int m, int n, int k) {
        boolean[][] vis = new boolean[m][n];
        return dfs(0, 0, k, m, n, vis);
    }

    public boolean check(int x, int y, int k, int n, int m, boolean[][]vis) {
        if(x < 0 || x >= n || y < 0 || y >= m || vis[x][y] == true) return false;
        int num = 0;
        String a = Integer.toString(x);
        for(int i = 0; i < a.length(); i++)
            num = num + a.charAt(i) - '0';
        String b = Integer.toString(y);
        for(int i = 0; i < b.length(); i++)
            num = num + b.charAt(i) - '0';
        return num <= k;
    }


    public int dfs(int x, int y, int k, int n, int m, boolean[][] vis) {
        if(!check(x, y, k, n, m, vis)) return 0;
        vis[x][y] = true;
        return 1 + dfs(x + 1, y, k, n, m, vis) + dfs(x, y + 1, k, n, m, vis);
    }

}
```

**bfs：**

```java
class Solution {

    Queue<int[]> q = new LinkedList<int[]>();
    int[][] moven = {{1, 0}, {0, 1}};
    
    public int movingCount(int m, int n, int k) {
        boolean[][] vis = new boolean[m][n];
        int ans = 1;
        q.add(new int[]{0, 0});
        while(!q.isEmpty()) {
            int[] tmp = q.poll();
            for(int i = 0; i < 2; i++) {
                int x = tmp[0] + moven[i][0];
                int y = tmp[1] + moven[i][1];
                if(x < 0 || x >= m) continue;
                if(y < 0 || y >= n) continue;
                if(cal(x) + cal(y) > k || vis[x][y] == true) continue;
                ans++;
                vis[x][y] =true;
                q.add(new int[]{x, y});
            }
        }
        return ans;
    }
    
    public int cal(int x) {
        int sum = 0;
        while(x != 0) {
            sum += x % 10;
            x /= 10;
        }
        return sum;
    }

}
```