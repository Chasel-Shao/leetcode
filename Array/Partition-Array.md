## Partition Array

----
## 题目地址

[https://www.lintcode.com/problem/partition-array](https://www.lintcode.com/problem/partition-array)

## 题目描述

```text
Given an array nums of integers and an int k, partition the array (i.e move the elements in "nums") such that:

All elements < k are moved to the left
All elements >= k are moved to the right
Return the partitioning index, i.e the first index i nums[i] >= k.
```

## 代码

### Approach #1 单指针索引交换

```java
public class Solution {
    public int partitionArray(int[] nums, int k) {
    int right = 0;
    int size = nums.length;
    for (int i = 0; i < size; i++) {
      if (nums[i] < k) {
         if (i != right) {
             int temp = nums[i];
             nums[i] = nums[right];
             nums[right] = temp;
          }
        ++right;
      }
    }

    return right;
  }
}
```

### Approach #2 双指针交换

```java
public class Solution {
  public int partitionArray(int[] nums, int k) {
    int left = 0;
    int right = nums.length - 1;
    while (left <= right) {
      while (left <= right && nums[left] < k) left++;
      while (left <= right && nums[right] >= k) right--;
      if (left <= right) {
        int temp = nums[left];
        nums[left] = nums[right];
        nums[right] = temp;
        ++left;
        --right;
      }
    }

    return left;
  }
}
```

