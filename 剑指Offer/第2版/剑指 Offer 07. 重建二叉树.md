**题意：** 输入某二叉树的前序遍历和中序遍历的结果，请构建该二叉树并返回其根节点。

假设输入的前序遍历和中序遍历的结果中都不含重复的数字。

**题解：**

因为前序遍历是 根->左->右的顺序，中序遍历是左->根->右的顺序，所以我们可以根据前序遍历在中序遍历中找到左右子树，然后一直递归下去。

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

    TreeNode root;
    HashMap<Integer, Integer> mp = new HashMap<Integer, Integer>();

    public TreeNode buildTree(int[] preorder, int[] inorder) {
        if(preorder.length == 0) return null;
        for(int i = 0; i < inorder.length; i++)
            mp.put(inorder[i], i);
        return build(0, 0, preorder.length - 1, preorder);
    }

    public TreeNode build(int root, int left, int right, int[] preorder) {
        if(left > right) return null;
        int i = mp.get(preorder[root]);
        TreeNode node = new TreeNode(preorder[root]);
        node.left = build(root + 1, left, i - 1, preorder);
        node.right = build(root + 1 + i - left, i + 1, right, preorder);
        return node;
    }
}
```