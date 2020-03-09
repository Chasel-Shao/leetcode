## Rehashing

----
## 题目地址

[https://www.lintcode.com/problem/rehashing](https://www.lintcode.com/problem/rehashing)

## 题目描述

```text
The size of the hash table is not determinate at the very beginning. If the total size of keys is too large (e.g. size >= capacity / 10), we should double the size of the hash table and rehash every keys. Say you have a hash table looks like below:

size=3, capacity=4

[null, 21, 14, null]
       ↓    ↓
       9   null
       ↓
      null
The hash function is:

int hashcode(int key, int capacity) {
    return key % capacity;
}
here we have three numbers, 9, 14 and 21, where 21 and 9 share the same position as they all have the same hashcode 1 (21 % 4 = 9 % 4 = 1). We store them in the hash table by linked list.

rehashing this hash table, double the capacity, you will get:

size=3, capacity=8

index:   0    1    2    3     4    5    6   7
hash : [null, 9, null, null, null, 21, 14, null]
Given the original hash table, return the new hash table after rehashing .
```

## 代码

```java
public class ListNode {
  int val;
  ListNode next;
  ListNode(int x) {
    this.val = x;
    next = null;
  }
}

public class Solution {
    public ListNode[] rehashing(ListNode[] hashTable) {
    if (hashTable.length <= 0) return hashTable;
    int newcapacity = 2 * hashtable.length;
    ListNode[] newTable = new ListNode[newcapacity];
    for (int i = 0; i < hashTable.length; i++) {
      ListNode node = hashTable[i];
      while (node != null) {
        int newIndex = (node.val % newcapacity + newcapacity) % newcapacity;
        if (newTable[newIndex] == null) {
          newTable[newIndex] = new ListNode(node.val);
        } else {
          ListNode dummy = newTable[newIndex];
          while (dummy.next != null) {
            dummy = dummy.next;
          }
          dummy.next = new ListNode(node.val);
        }
        node = node.next;
      }
    }
    return newTable;
  }
}
```

