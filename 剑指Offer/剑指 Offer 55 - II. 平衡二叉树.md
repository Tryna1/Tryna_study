**题意：** 输入一棵二叉树的根节点，判断该树是不是平衡二叉树。如果某二叉树中任意节点的左右子树的深度相差不超过1，那么它就是一棵平衡二叉树。

**题解：** 
* 如果这棵树是平衡二叉树，那么它左右两棵子树高度差不超过1，同时这棵树的高度为左右两棵子树高度的最大值+1
* 采用后序遍历从底至上返回子树的高度，比较左右子树的高度判断是否是平衡二叉树。

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
    public boolean isBalanced(TreeNode root) {
        return dfs(root) != -1;
    }

    public int dfs(TreeNode now) {
        if(now == null) return 0;
        int left = dfs(now.left);
        if(left == -1) return -1;
        int right = dfs(now.right);
        if(right == -1) return -1;
        return Math.abs(left - right) <= 1 ? Math.max(left, right) + 1 : -1;
    }
}
```