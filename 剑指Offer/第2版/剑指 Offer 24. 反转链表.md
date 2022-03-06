**题意：** 定义一个函数，输入一个链表的头节点，反转该链表并输出反转后链表的头节点。

**题解：** 要求反转链表，还是很容易想到使用栈，反转后的链表通过栈来连接。

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
    public ListNode reverseList(ListNode head) {
        Stack<Integer> st = new Stack<Integer>();
        while(head != null) {
            st.push(head.val);
            head = head.next;
        }
        ListNode Head = new ListNode(0);
        ListNode cur = Head;
        while(!st.empty()) {
            cur.next = new ListNode(st.pop());
            cur = cur.next;
        }
        return Head.next;
    }
}
```