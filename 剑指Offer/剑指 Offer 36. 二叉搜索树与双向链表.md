**题意：** 输入一棵二叉搜索树，将该二叉搜索树转换成一个排序的循环双向链表。要求不能创建任何新的节点，只能调整树中节点指针的指向。

**题解：** 因为是二叉搜索树，又要求生成的链表排序，故很容易想到使用中序遍历。同时记录一下上一个结点是什么，连接两个结点即可。注意是双向循环链表，故头尾还需要连接。

```java
/*
// Definition for a Node.
class Node {
    public int val;
    public Node left;
    public Node right;

    public Node() {}

    public Node(int _val) {
        val = _val;
    }

    public Node(int _val,Node _left,Node _right) {
        val = _val;
        left = _left;
        right = _right;
    }
};
*/
class Solution {

    Node last = null;
    Node head = null;

    public Node treeToDoublyList(Node root) {
        if(root == null) return root;
        dfs(root, null);
        head.left = last;
        last.right = head;
        return head;
    }

    public void dfs(Node now, Node fa) {
        if(now == null) return ;
        dfs(now.left, now);
        if(last != null) {
            last.right = now;
            now.left = last;
        }
        else head = now;
        last = now;
        dfs(now.right, now);
    }
}
```