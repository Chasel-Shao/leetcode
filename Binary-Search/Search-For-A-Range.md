## Search For A Range

----
## 题目地址

[http://www.lintcode.com/problem/search-for-a-range/description](http://www.lintcode.com/problem/search-for-a-range/description)

## 题目描述

```text
Given a sorted array of n integers, find the starting and ending position of a given target value.

If the target is not found in the array, return [-1, -1].

Example
Example 1:

Input:
[]
9
Output:
[-1,-1]

Example 2:

Input:
[5, 7, 7, 8, 8, 10]
8
Output:
[3, 4]
Challenge
O(log n) time.
```

## 解题思路

Binary Search

## 代码

```java
public class Solution {
    public int[] searchRange(int[] A, int target) {
    if (A.length == 0) return new int[]{-1, -1};

    int start, end, mid;
    int[] bound = new int[2];

    start = 0;
    end = A.length - 1;
    while (start + 1 < end) {
      mid = start + (end - start) / 2;
      if (A[mid] == target) {
        end = mid;    // difference
      } else if (A[mid] < target) {
        start = mid;
      } else {
        end = mid;
      }
    }

    if (A[start] == target) {
      bound[0] = start;
    } else if (A[end] == target) {
      bound[0] = end;
    } else {
      bound[0] = bound[1] = -1;
      return bound;
    }

    start = 0;
    end = A.length - 1;
    while (start + 1 < end) {
      mid = start + (end - start) / 2;
      if (A[mid] == target) {
        start = mid; // difference
      } else if (A[mid] < target) {
        start = mid;
      } else {
        end = mid;
      }
    }
    if (A[end] == target) {
      bound[1] = end;
    } else if (A[start] == target) {
      bound[1] = start;
    } else {
      bound[0] = bound[1] = -1;
      return bound;
    }

    return bound;
  }

}
```

