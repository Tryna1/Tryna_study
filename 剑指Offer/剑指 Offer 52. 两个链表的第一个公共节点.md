**题意：** 输入两个链表，找出它们的第一个公共节点。

**题解：** 遍历一遍两个链表，当A链表遍历完使这个指针去遍历B链表，同理当B链表遍历完使这个指针去遍历A链表，当两个结点相等时就是他们的公共点。

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        ListNode A = headA, B = headB;
        while(A != B) {
            A = A != null ? A.next : headB;
            B = B != null ? B.next : headA;
        }
        return A;
    }
}
```