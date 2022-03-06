**题意：** 给你二叉树的根节点 `root` 和一个整数目标和 `targetSum` ，找出所有 从根节点到叶子节点 路径总和等于给定目标和的路径。

**题解：** dfs遍历这棵树即可。然后记录路径的时候不能直接`add(tmp)`，这相当于加入了这个对象，后续这个对象改变时，加入的路径也会改变，应该**new**一个新的`List`。

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {

    LinkedList<List<Integer>> res = new LinkedList<List<Integer>>();
    LinkedList<Integer> tmp = new LinkedList<Integer>();

    public List<List<Integer>> pathSum(TreeNode root, int target) {
        dfs(root, 0, target);
        return res;
    }

    public void dfs(TreeNode now, int sum, int target) {
        if(now == null) return ;
        tmp.add(now.val);
        if(now.left == null && now.right == null && sum + now.val == target) {
            res.add(new LinkedList(tmp));
        }
        dfs(now.left, sum + now.val, target);
        dfs(now.right, sum + now.val, target);
        tmp.removeLast();
    }
}
```