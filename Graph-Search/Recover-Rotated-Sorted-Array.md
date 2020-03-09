## Recover Rotated Sorted Array

----
## 题目地址

[http://www.lintcode.com/problem/recover-rotated-sorted-array/](http://www.lintcode.com/problem/recover-rotated-sorted-array/)

[http://www.jiuzhang.com/solutions/recover-rotated-sorted-array](http://www.jiuzhang.com/solutions/recover-rotated-sorted-array)

## 题目描述

```text
Given a rotated sorted array, recover it to sorted array in-place.（Ascending）
```

## 代码

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

