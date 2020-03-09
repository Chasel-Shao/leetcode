## Minimum Adjustment Cost

----
## 题目地址

[https://www.lintcode.com/problem/minimum-adjustment-cost/description](https://www.lintcode.com/problem/minimum-adjustment-cost/description)

## 题目描述

```text
Given an integer array, adjust each integers so that the difference of every adjacent integers are not greater than a given number target.

You can assume each number in the array is a positive integer and not greater than 100.
```

## 代码

```java
public class Solution {
    public static int M = 100;
  public int minAdjustmentCost(int A[], int n, int target) {
    if (A == null || A.size() == 0) return 0;
    int[][] dp = new int[n][M + 1];

    for (int j = 0; j <= M; j++) {
      dp[0][j] = Math.abs(j - A[0]);
    }

    for (int i = 1; i < n; i++) {
      for (int j = 0; i <= M; j++) {
        dp[i][j] = Integer.MAX_VALUE;
           int end = Math.min(j + target, 100); 
        int start = Math.max(0, j - target)
        // k => [j - target, j + target]
        for (int k = start; k <= end; k++) {
          dp[i][j] = Math.min(dp[i][j], dp[i - 1][k] + Math.abs(j - A[i]));
        }
      }
    }

    int min = Integer.MAX_VALUE;
    for (int j = 0; j <= M; j++) {
      min = Math.min(res, dp[n - 1][j]);
    }
    return min;
  }
}
```

