## Maximum Subarray Difference

----
## 题目地址

[https://www.lintcode.com/problem/maximum-subarray-difference/description](https://www.lintcode.com/problem/maximum-subarray-difference/description)

## 题目描述

```text
Given an array with integers.

Find two non-overlapping subarrays A and B, which |SUM(A) - SUM(B)| is the largest.

Return the largest difference.
```

## 代码

```java
public class Solution {
    public int maxDiffSubArrays (int[] nums) {
    int size = nums.length;
    int[] left_max = new int[size];
    int[] left_min = new int[size];
    int[] right_max = new int[size];
    int[] right_min = new int[size];
    int[] copy = new int[size];

    for(int i = 0; i < size; i++) {
      copy[i] = -1 * nums[i];
    }
    // Forward : get max subarray
    int max = Integer.MIN_VALUE;
    int sum = 0;
    int minSum = 0;
    for (int i = 0; i < size; i++) {
      sum += nums[i];
      max = Math.max(max, sum - minSum);
      minSum = Math.min(minSum, sum);
      left_max[i] = max;
    }
    // Backward: get max subbary
    max = Integer.MIN_VALUE;
    sum = 0;
    minSum = 0;
    for (int i = size - 1; i >= 0; i--) {
      sum += nums[i];
      max = Math.max(max, sum - minSum);
      minSum = Math.min(minSum, sum);
      right_max[i] = max;
    }

    // Forward: get min subarray
    max = Integer.MIN_VALUE;
    sum = 0;
    minSum = 0;
    for (int i = 0; i < size; i++) {
      sum += copy[i];
      max = Math.max(max, sum - minSum);
      minSum = Math.min(sum, minSum);
      left_min[i] = -1 * max;
    }
    // Backward: get min subarray
    max = Integer.MIN_VALUE;
    sum = 0;
    minSum = 0;
    for (int i = size - 1; i >= 0; i--) {
      sum += copy[i];
      max = Math.max(max, sum - minSum);
      minSum = Math.min(sum, minSum);
      right_min[i] = -1 * max;
    }

    int diff = 0;
    for (int i = 0; i < size; i++) {
      diff = Math.max(diff, Math.abs(left_max[i] - right_min[i]));
      diff = Math.max(diff, Math.abs(left_min[i] - right_max[i]));
    }

    return diff;
  }
}
```

