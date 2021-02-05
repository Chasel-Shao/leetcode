## Coins In A Line Iii

----
## 题目地址

https://www.lintcode.com/problem/coins-in-a-line/
https://zhengyang2015.gitbooks.io/lintcode/coins_in_a_line_iii_396.html

## 题目描述

```text
There are n coins in a line. Two players take turns to take a coin from one of the ends of the line until there are no more coins left. The player with the larger amount of money wins.

Could you please decide the first player will win or lose?

Example:
Given array A = [3,2,2], return true.
Given array A = [1,2,4], return true.
Given array A = [1,20,4], return false.
```

## 代码

### Approach #1 DP

```JAVA
public class Solution {
  public boolean firstWillWin(int[] values) {
    int n = values.length;
    int[] sum = new int[n + 1];
    sum[0] = 0;

    for (int i = 1; i <= n; i++) /* Get the sum in ith index */
      sum[i] = sum[i - 1] + values[i - 1];

    int[][] dp = new int[n][n];
    for (int i = 0; i < n; i++) 
      dp[i][i] = values[i]; /* Treat these like the leaf nodes */

    for (int len = 2; len <= n; len++) {
      for (int i = 0; i < n; i++) {
        int j = i + len - 1;
        if (j >= n) continue;
        int s = sum[j + 1] - sum[i];
        dp[i][j] = Math.max(s - dp[i + 1][j], s - dp[i][j - 1]);
      }
    }

    return dp[0][n - 1] > sum[n] / 2;
  }
}

```

### Approach #2 DFS

`dp[start][end] =>  [values[start-1], values[end-1]]`

```JAVA
public class Solution {
    /**
     * @param values: an array of integers
     * @return: a boolean which equals to true if the first player will win
     */
    public boolean firstWillWin(int[] values) {
        // write your code here
        if (values == null || values.length == 0){
            return false;
        }

        int n = values.length;
        int[] sum = new int[n + 1];
        sum[0] = 0;
        for (int i = 1; i <= n; i++){
            sum[i] = sum[i - 1] + values[i - 1];
        }
        int[][] dp = new int[n + 1][n + 1];
        boolean[][] visit = new boolean[n + 1][n + 1];

        return search(1, n, sum, dp, visit) > sum[n] / 2;
    }

    private int search(int start, int end, int[] sum, int[][] dp, boolean[][] visit){
        if (visit[start][end]) {
            return dp[start][end];
        }

        if (start == end) {
            visit[start][end] = true;
            return dp[start][end] = sum[end] - sum[start - 1];
        }

        int max = (sum[end] - sum[start - 1]) - Math.min(search(start, end - 1, sum, dp, visit), search(start + 1, end, sum, dp, visit));

        visit[start][end] = true;
        dp[start][end] = max;
        return dp[start][end];
    }
}
```

