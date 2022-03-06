**题意：** 输入一个链表，输出该链表中倒数第k个节点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾节点是倒数第1个节点。

例如，一个链表有 6 个节点，从头节点开始，它们的值依次是 1、2、3、4、5、6。这个链表的倒数第 3 个节点是值为 4 的节点。


**题解：** 第一时间想到的是两次循环的方法，第一次遍历一遍链表记录总长度，第二次遍历到第$len - k$个位置然后输出后面的链表。

使用双指针可以只用一次循环，记录两个指针`left`、`right`，让这两个指针之前的距离为$k$，遍历到链表尾输出`left`即可。

```java
class Solution {
    public ListNode getKthFromEnd(ListNode head, int k) {
        int tot = 0;
        ListNode left = head, right = head;
        while(right != null) {
            if(tot >= k) left = left.next;
            tot++;
            right = right.next;
        }
        return left;
    }
}
```