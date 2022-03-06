**题意：** 输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

**题解：** 因为我们知道栈是先进后出的特点，符合本题的倒序输出，所以使用栈可以轻松解出本题。

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
    public int[] reversePrint(ListNode head) {
        Stack<Integer> st = new Stack<Integer>();
        while(head != null) {
            st.push(head.val);
            head = head.next;
        }
        int sz = st.size();
        int a[] = new int[sz];
        for(int i = 0; i < sz; i++) {
            a[i] = st.pop();
        }
        return a;
    }
}
```