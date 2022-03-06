**题意：** 请实现两个函数，分别用来序列化和反序列化二叉树。

你需要设计一个算法来实现二叉树的序列化与反序列化。这里不限定你的序列 / 反序列化算法执行逻辑，你只需要保证一个二叉树可以被序列化为一个字符串并且将这个字符串反序列化为原始的树结构。

提示：输入输出格式与 LeetCode 目前使用的方式一致，详情请参阅 LeetCode 序列化二叉树的格式。你并非必须采取这种方式，你也可以采用其他的方法解决这个问题。

**题解：** 使用两个层序遍历即可解决


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
public class Codec {

    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
        if(root == null) return "[]";
        LinkedList<TreeNode> q = new LinkedList<>();
        StringBuilder res = new StringBuilder("[");
        q.add(root);
        while(!q.isEmpty()) {
            TreeNode tmp = q.remove();
            
            if(tmp == null) {
                res.append("null,");
            }
            else{
                res.append(tmp.val + ",");
                q.add(tmp.left); q.add(tmp.right);
            }
            
        }
        res.deleteCharAt(res.length() - 1);
        res.append(']');
        return res.toString();
    }

    // Decodes your encoded data to tree.
    public TreeNode deserialize(String data) {
        if(data.equals("[]")) return null;
        String[] val = data.substring(1, data.length() - 1).split(",");
        TreeNode root = new TreeNode(Integer.parseInt(val[0]));
        LinkedList<TreeNode> q = new LinkedList<>();
        q.add(root);
        int i = 1;
        while(!q.isEmpty()) {
            TreeNode tmp = q.remove();
            if(!val[i].equals("null")) {
                tmp.left = new TreeNode(Integer.parseInt(val[i]));
                q.add(tmp.left);
            }
            i++;
            if(!val[i].equals("null")) {
                tmp.right = new TreeNode(Integer.parseInt(val[i]));
                q.add(tmp.right);
            }
            i++;
        }
        return root;
    }
}

// Your Codec object will be instantiated and called as such:
// Codec codec = new Codec();
// codec.deserialize(codec.serialize(root));
```