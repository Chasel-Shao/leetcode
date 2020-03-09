## Maximum Subarray Iii

----
## 题目地址

[https://www.lintcode.com/problem/maximum-subarray-iii/description](https://www.lintcode.com/problem/maximum-subarray-iii/description)

## 题目描述

```text
Given an array of integers and a number k, find k non-overlapping subarrays which have the largest sum.

The number in each subarray should be contiguous.

Return the largest sum.
```

## 代码

```java
public class Solution {
    public int maxSubArray(int[] nums, int k) {
    if (nums.length < k) return 0;
    int n = nums.length;
       int[][] globalMax = new int[k + 1][n + 1];
    int[][] localMax = new int[k + 1][n + 1];

    for (int i = 1; i <= k; i++) {
      localMax[i][i - 1] = Integer.MIN_VALUE;
      globalMax[i][i - 1] = Integer.MIN_VALUE;
      for (int j = i; j < n; j++) {
        localMax[i][j] = Math.max(localMax[i][j - 1], globalMax[i - 1][j - 1]) + nums[j - 1];
        globalMax[i][j] = Math.max(globalMax[i][j - 1], localMax[i][j]);
      }
    }

    return globalMax[k][n];
  }
}
```

