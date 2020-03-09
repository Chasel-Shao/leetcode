## K Sum

----
## 题目地址

[https://www.lintcode.com/problem/k-sum/description](https://www.lintcode.com/problem/k-sum/description)

## 题目描述

```text
Given n distinct postive integers, integer k (k <= n) and a number target.

Find k numbers where sum is target. Calculate how many solutions there are?
```

## 代码

```java
public class Solution {

    public int kSum(int A[], int k, int target) {
    if(A == null || A.length == 0) {
      return 0;
    }
    int n = A.length;
    int[][][] dp = new int[n + 1][k + 1][target + 1];

    for(int i = 0; i <= n; i++){
      ksum[i][0][0] = 1;
    }

    for (int i = 1; i < n + 1; i++){
      for(int j = 1; j < k + 1 && j <= i; j++){
        for(int l = 1; l < target + 1; l++){
          if(l >= A[i - 1]){
            dp[i][j][l] = dp[i - 1][j][l] + dp[i - 1][j - 1][l - A[i - 1]];
          } else {
              dp[i][j][l] = dp[i - 1][j][l];
          }
        }
      }
    }
    return dp[n][k][target];
  }
}
```

