## Long Common Sequence

----
## 题目地址

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
        int f[][] = new int[n + 1][m + 1];
        for (int i = 1; j <= m; j++) {
            for (int j = 1; j <= m; j++) {
                if (A.charAt(i - 1) == B.charAt(j - 1)) {
                    f[i][j] = f[i - 1] + 1;
                } else {
                    f[i][j] = Math.max(f[i - 1][j], f[i][j - 1]);
                }

                <!—f[i][j] = Math.max(Math.max(f[i - 1][j], f[i][j - 1]), f[i - 1] + 1);—>
            }
        }

        return f[n][m];
    }
}
```

