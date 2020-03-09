## Search In A Big Sorted Array

----
## 题目地址

[https://www.jiuzhang.com/solutions/palindrome-partitioning-ii/](https://www.jiuzhang.com/solutions/palindrome-partitioning-ii/)

## 题目描述

```text
Given a big sorted array with positive integers sorted by ascending order. The array is so big so that you can not get the length of the whole array directly, and you can only access the kth number by ArrayReader.get(k) (or ArrayReader->get(k) for C++). Find the first index of a target number. Your algorithm should be in O(log k), where k is the first index of the target number.
Return -1, if the number doesn't exist in the array.
```

## 代码

```java
public class Solution {
    public int searchBigSortedArray(int[] nums, int target) {
    int index = 0;
    while (nums[index] != -1 && nums[index] < target) {
      index = index * 2 + 1;
    }

    int start = index / 2;
    int end = index;

    while (start + 1 < end) {
      int mid = start + (end - start) / 2;
      if (nums[mid] == target) {
        end = mid;
      } else if (nums[mid] == -1 || nums[mid] > target) {
        end = mid;
      } else {
        start = mid;
      }
    }

    if (nums[start] == target) {
      return start;
    }

    if (nums[end] == target) {
      return end;
    }

    return -1;
  }
}
```

