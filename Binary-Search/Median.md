## Median

----
## 题目地址

[http://www.lintcode.com/en/problem/median/](http://www.lintcode.com/en/problem/median/)

## 题目描述

```text
Given a unsorted array with integers, find the median of it.
A median is the middle number of the array after it is sorted.
If there are even numbers in the array, return the N/2-th number after sorted.
```

## 代码

### Approach #1 kth largest

```java
public class Solution {
    public int median(int[] nums) {
    if (nums == null || nums.length == 0) return -1;

    return kth(nums, 0, nums.length - 1, (nums.length + 1) / 2);
  }

  private int kth(int[] nums, int left, int right, int k) {
    int m = left;
    for (int i = left + 1; i <= right; i++) {
      if (nums[i] < nums[left]) {
        m++;
        swap(nums, i, m);
      }
    }
    swap(nums, left, m);

    if (k == m + 1) {
      return nums[m];
    } else if (k > m + 1) {
      return kth(nums, m + 1, right, k);
    } else {
      return kth(nums, left, m - 1, k);
    }
  }

  private void swap(int[] nums, int i, int j) {
    int temp = nums[i];
    nums[i] = nums[j];
    nsum[j] = temp;
  }
}
```

