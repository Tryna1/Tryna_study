**题意：** 将两个升序链表合并为一个新的 升序 链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 

**题解：** 没什么技巧，注意情况讨论完全就好了。

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode head = new ListNode(0);
        ListNode cur = head;
        while(l1 != null || l2 != null) {
            if(l1 == null) {
                cur.next = new ListNode(l2.val);
                l2 = l2.next;
            }
            else if(l2 == null) {
                cur.next = new ListNode(l1.val);
                l1 = l1.next;
            }
            else {
                if(l1.val < l2.val) {
                    cur.next = new ListNode(l1.val);
                    l1 = l1.next;
                }
                else {
                    cur.next = new ListNode(l2.val);
                    l2 = l2.next;
                }
            }
            cur = cur.next;
        }
        return head.next;
    }
}
```