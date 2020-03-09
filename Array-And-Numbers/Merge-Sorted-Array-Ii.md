## Merge Sorted Array Ii

----
## 题目地址

[https://www.lintcode.com/problem/merge-sorted-array/description](https://www.lintcode.com/problem/merge-sorted-array/description)

## 题目描述

```text
Merge two given sorted integer array A and B into a new sorted integer array.

Example
A=[1,2,3,4]

B=[2,4,5,6]

return [1,2,2,3,4,4,5,6]

Challenge
How can you optimize your algorithm
if one array is very large and the other is very small?
```

## 代码

```java
public class Solution {
    public ArrayList<Integer> mergeSortedArray(ArrayList<Integer> A, ArrayList<Integer> B) {
    if (A == null || A.isEmpty()) return B;
    if (B == null || B.isEmpty()) return A;

    ArrayList<Integer> C = new ArrayList<Integer>();
    int aLen = A.size(), bLen = B.size();
    int i = 0, j = 0;
    while (i < aLen && j < bLen) {
      if (A.get(i) < B.get(j)) {
        C.add(A.get(i));
        i++;
      } else {
        C.add(B.get(j));
        j++;
      }
    }

    while (i < aLen) {
      C.add(A.get(i));
      i++;
    }

    while (j < bLen) {
      C.add(B.get(j));
      j++;
    }

    return C;
  }
}
```

