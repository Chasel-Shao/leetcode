## Maximum Subarray Iii

----
## 题目地址

[https://www.lintcode.com/problem/maximum-subarray-iii/description](https://www.lintcode.com/problem/maximum-subarray-iii/description)

[https://zhengyang2015.gitbooks.io/lintcode/maximum\_subarray\_iii\_43.html\#](https://zhengyang2015.gitbooks.io/lintcode/maximum_subarray_iii_43.html#)

## 题目描述

```text
Given an array of integers and a number k, find k non-overlapping subarrays which have the largest sum.

The number in each subarray should be contiguous.
```

## 代码

```java
public class Solution {
    public int maxSubArray(int[] nums, int k){
    if(nums.length < k) {
      return 0;
    }

    int len = nums.length;
    int[][] localMax = new int[len + 1][k + 1];
    int[][] globalMax = new int[len + 1][k + 1];

    for(int j = 1; j <= k; j++) {
      localMax[j - 1][j] = Integer.MIN_VALUE;

      for(int i = j; i <= len; i++){
        localMax[i][j] = Math.max(globalMax[i - 1][j - 1], 
                                 localMax[i - 1][j]) + nums[i - 1];
        if(i == j) {
          globalMax[i][j] = localMax[i][j];
        } else {
          globalMax[i][j] = Math.max(globalMax[i - 1][j], 
                                    localMax[i][j]);
        }
      }
    }

    return globalMax[len][k];
  }
}
```

