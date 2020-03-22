## Remove Duplicates From Unsorted List Geeksforgeeks

----
## 题目地址

[https://www.geeksforgeeks.org/remove-duplicates-from-an-unsorted-linked-list/](https://www.geeksforgeeks.org/remove-duplicates-from-an-unsorted-linked-list/)

## 题目描述

```text
Write a removeDuplicates() function which takes a list and deletes
any duplicate nodes from the list. The list is not sorted.

For example if the linked list is 12->11->12->21->41->43->21,
then removeDuplicates() should convert the list to 12->11->21->41->43.

If temporary buffer is not allowed, how to solve it?
```

## 代码

### Approach #1 Two loop

```java
public class Solution {
    public ListNode deleteDuplicates(ListNode head) {
    if (head == null) return null;

    ListNode curr = head;
    while (curr != null) {
      ListNode inner = curr;
      while (inner.next != null) {
        if (inner.next.val == curr.val) {
          inner.next = inner.next.next;
        } else {
          inner = inner.next;
        }
      }
      curr = curr.next;
    }

    return head;
  }
}
```

