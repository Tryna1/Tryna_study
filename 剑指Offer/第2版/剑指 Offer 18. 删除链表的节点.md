**题意：** 给定单向链表的头指针和一个要删除的节点的值，定义一个函数删除该节点。

**题解：** 其实不用双指针，简单来说就是实现`LinkedList`的`remove`方法，遍历一遍链表即可。

```java
class Solution {
    public ListNode deleteNode(ListNode head, int val) {
        if(head.val == val) return head.next;
        ListNode cur = head;
        while(head != null) {
            if(head.next == null) break;
            if(head.next.val == val) {
                head.next = head.next.next;
            }
            head = head.next;
        }
        return cur;
    }
}
```