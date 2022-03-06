**题意：** 输入一棵二叉树的根节点，求该树的深度。从根节点到叶节点依次经过的节点（含根、叶节点）形成树的一条路径，最长路径的长度为树的深度。

**题解：** 求二叉树的深度，递归并且记录深度即可。

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {

    int ans = 0;

    public int maxDepth(TreeNode root) {
        dfs(root, 1);
        return ans;
    }

    public void dfs(TreeNode now, int dep) {
        if(now == null) return ;
        ans = Math.max(ans, dep);
        dfs(now.left, dep + 1);
        dfs(now.right, dep + 1);
    }
}
```