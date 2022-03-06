**题意：** 从上到下打印出二叉树的每个节点，同一层的节点按照从左到右的顺序打印。

**题解：** 使用BFS求层序遍历

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int x) { val = x; }
}

class Solution {

    Queue<TreeNode> q = new LinkedList<TreeNode>();
    ArrayList<Integer> res = new ArrayList<Integer>();
    public int[] levelOrder(TreeNode root) {
        if(root != null) {
            q.add(root);
            while(!q.isEmpty()) {
                TreeNode tmp = q.peek();
                q.remove();
                res.add(tmp.val);
                if(tmp.left != null)
                    q.add(tmp.left);
                if(tmp.right != null)
                    q.add(tmp.right);
            }
        }
        int[] ans = new int[res.size()];
        for(int i = 0; i < res.size(); i++)
            ans[i] = res.get(i);
        return ans;
    }
}
```