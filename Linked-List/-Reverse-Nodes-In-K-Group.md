##  Reverse Nodes In K Group

----
## 题目地址

[https://www.lintcode.com/problem/reverse-nodes-in-k-group/description](https://www.lintcode.com/problem/reverse-nodes-in-k-group/description)

## 题目描述

```text
Given a linked list, reverse the nodes of a linked list k at a time and return its modified list.

If the number of nodes is not a multiple of k then left-out nodes in the end should remain as it is.

You may not alter the values in the nodes, only nodes itself may be changed.
Only constant memory is allowed.
```

## 代码

```java
public class Solution {

  public ListNode reverseKGroup(ListNode head, int k) {
    if (head == null || k <= 1) return head;

    ListNode dummy = new ListNode(0);
    dummy.next = head;

    head = dummy;
    while (head.next != null) {
      head = reverseNextK(head, k);
    }

    return dummy.next;
  }

  private ListNode reverseNextK(ListNode head, int k) {
    ListNode next = head;
    for (int i = 0; i < k; i++) {
      if (next.next == null) return next;

      next = next.next;
    }

    ListNode n1 = head.next;
    ListNode prev = head, curt = n1;
    for (int i = 0; i < k; i++) {
      ListNode temp = curt.next;
      curt.next = prev;
      prev = curt;
      curt = temp;
    }

    n1.next = curt;
    head.next = prev;
    return n1;
  }
}
```

