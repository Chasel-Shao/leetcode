## Longest Common Sequence

----
## 题目地址

https://leetcode.com/problems/longest-common-subsequence/

[https://www.jiuzhang.com/solutions/longest-common-subsequence/](https://www.jiuzhang.com/solutions/longest-common-subsequence/)

## 题目描述

```text
Given two strings, find the longest common subsequence (LCS).

You code should return the length of LCS.
```

## 代码

```java
public class Solution {
  public int longestCommonSubsequence(String A, String B) {
		int n = A.length();
    int m = B.length();
        
    // state: dp[i][j]表示表示A序列前i个，与B序列的前j个的LCS长度
    // initialization: 初始值为0
    int dp[][] = new int[n + 1][m + 1];

    // function
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= m; j++) {
            dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
            if (A.charAt(i - 1) == B.charAt(j - 1)) {
                dp[i][j] = Math.max(dp[i][j], dp[i - 1][j - 1] + 1);
            }
        }
    }

    // answer
    return dp[n][m];
  }
}
```

