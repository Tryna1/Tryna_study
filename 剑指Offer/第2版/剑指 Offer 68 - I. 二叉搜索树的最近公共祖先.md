**题意：** 给定一个二叉搜索树, 找到该树中两个指定节点的最近公共祖先。

**题解：** 因为是二叉搜索树，所以左孩子都小于根，右孩子都大于根，所以从上到下找根即可。

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
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(p.val < root.val && q.val < root.val)
            return lowestCommonAncestor(root.left, p, q);
        else if(p.val > root.val && q.val > root.val)
            return lowestCommonAncestor(root.right, p, q);
        else return root;
    }
}
```