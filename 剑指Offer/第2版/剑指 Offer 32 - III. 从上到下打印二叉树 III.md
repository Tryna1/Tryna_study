**题意：** 请实现一个函数按照之字形顺序打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推。

**题解：** 比起上一道题，这题多了一个奇偶层的顺序问题，故考虑使用双端队列实现。

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
    public List<List<Integer>> levelOrder(TreeNode root) {
        Deque<TreeNode> q = new LinkedList<>();
        List<List<Integer>> ans = new ArrayList<>();
        int cnt = 1;
        if(root != null) {
            q.addFirst(root);
            while(!q.isEmpty()) {
                List<Integer> res = new ArrayList<>();
                int sz = q.size();
                for(int i = 1; i <= sz; i++) {
                    TreeNode tmp;
                    if(cnt % 2 == 1)
                        tmp = q.removeFirst();
                    else tmp = q.removeLast();
                    res.add(tmp.val);
                    if(cnt % 2 == 1) {
                        if(tmp.left != null)
                            q.addLast(tmp.left);
                        if(tmp.right != null)
                            q.addLast(tmp.right);
                    }
                    else {
                        if(tmp.right != null)
                            q.addFirst(tmp.right);
                        if(tmp.left != null)
                            q.addFirst(tmp.left);
                    }
                }
                cnt++;
                ans.add(res);
            }
        }
        return ans;
    }
}
```