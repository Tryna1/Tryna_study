**题意：** 输入两棵二叉树A和B，判断B是不是A的子结构。(约定空树不是任意一个树的子结构)

B是A的子结构， 即 A中有出现和B相同的结构和节点值。

**题解：** 
* B是A的子结构
* B是A的左子树的子结构
* B是A的右子树的子结构

递归下去即可。

然后再递归判断B是不是A的子树的子结构

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
    public boolean isSubStructure(TreeNode A, TreeNode B) {
        if(A == null && B != null) return false;
        if(A != null && B == null) return false;
        return (check(A, B) || isSubStructure(A.left, B) || isSubStructure(A.right, B));
    }

    public boolean check(TreeNode A, TreeNode B) {
        if(B == null) return true;
        if(A == null || A.val != B.val) return false;
        return (check(A.left, B.left) && check(A.right, B.right));
    }
}
```