## Recover Rotated Sorted Array

----
## 题目地址

[http://www.lintcode.com/problem/recover-rotated-sorted-array/](http://www.lintcode.com/problem/recover-rotated-sorted-array/)

[http://www.jiuzhang.com/solutions/recover-rotated-sorted-array](http://www.jiuzhang.com/solutions/recover-rotated-sorted-array)

## 题目描述

```text
Given a rotated sorted array, recover it to sorted array in-place.（Ascending）

Clarification
What is rotated array?

For example, the orginal array is [1,2,3,4], The rotated array of it can be [1,2,3,4], [2,3,4,1], [3,4,1,2], [4,1,2,3]
Example
Example1:
[4, 5, 1, 2, 3] -> [1, 2, 3, 4, 5]
Example2:
[6,8,9,1,2] -> [1,2,6,8,9]

Challenge
In-place, O(1) extra space and O(n) time.
```

## 代码

### Approach #1 Rcursive Reverse

```java
public class Solution {
  public void recoverRotatedSortedArray(ArrayList<Integer> nums) {
    for (int index = 0; index < nums.length.size() - 1; index++) {
      if (nums.get(index) > nums.get(index + 1)) {
        reverse(nums, 0, index);
        reverse(nums, index + 1, nums.size() - 1);
        reverse(nums, 0, nums.size() - 1);
        return;
      }
    }
  }


  private void reverse(ArrayList<Integer> nums, int start, int end) {
    for (int i = start, j = end; i < j; i++, j--) {
      int temp = nums.get(i);
      nums.set(i, nums.get(j));
      nums.set(j, temp);
    }
  }

}
```

