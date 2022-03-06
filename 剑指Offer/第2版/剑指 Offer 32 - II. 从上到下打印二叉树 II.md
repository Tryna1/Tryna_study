**题意；** 从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行。

**题解：** 跟上一题的区别就是要记录每层的元素，记录一下上一层元素的个数即可。

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int x) { val = x; }
}

class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        Queue<TreeNode> q = new LinkedList<TreeNode>();
        List<List<Integer>> res = new ArrayList<>();
        if(root != null) {
            q.add(root);
            while(!q.isEmpty()) {
                int sz = q.size();
                List<Integer> ans = new ArrayList<>();
                for(int i = 1; i <= sz; i++) {
                    TreeNode tmp = q.peek();
                    q.remove();
                    ans.add(tmp.val);
                    if(tmp.left != null)
                        q.add(tmp.left);
                    if(tmp.right != null)
                        q.add(tmp.right);
                }
                res.add(ans);
            }
        }
        return res;
    }
}
```