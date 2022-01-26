**题意：** 给定一棵二叉搜索树，请找出其中第 k 大的节点的值。

**题解：** 要求第$k$大，又是二叉搜索树，故采用中序遍历：右、root、左。

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

    int num, res;

    public int kthLargest(TreeNode root, int k) {
        num = k;
        dfs(root);
        return res;
    }

    public void dfs(TreeNode root) {
        if(root == null) return;
        dfs(root.right);
        num--;
        if(num == 0) res = root.val;
        dfs(root.left);
    }
}
```