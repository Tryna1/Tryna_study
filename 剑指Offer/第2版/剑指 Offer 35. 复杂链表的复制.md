**题意：** 请实现 copyRandomList 函数，复制一个复杂链表。在复杂链表中，每个节点除了有一个 next 指针指向下一个节点，还有一个 random 指针指向链表中的任意节点或者 null。


**题解：** 这题的一个难点就是不能遍历复制链表，因为复制random结点的时候会出现指向的结点还未创建的情况，所以可以采用map来构建新老结点的映射，先把所有的新节点都创建出来，然后再将它们连线。

```java
/*
// Definition for a Node.
class Node {
    int val;
    Node next;
    Node random;

    public Node(int val) {
        this.val = val;
        this.next = null;
        this.random = null;
    }
}
*/
class Solution {
    public Node copyRandomList(Node head) {
       Node cur = head;
       HashMap<Node, Node> mp = new HashMap<Node, Node>();
       while(cur != null) {
           mp.put(cur, new Node(cur.val));
           cur = cur.next;
       }
       cur = head;
       while(cur != null) {
           mp.get(cur).next = mp.get(cur.next);
           mp.get(cur).random = mp.get(cur.random);
           cur = cur.next;
       }
       return mp.get(head);
    }
}
```