## Coins In A Line Iii

----
## 题目地址

[https://zhengyang2015.gitbooks.io/lintcode/coins\_in\_a\_line\_iii\_396.html](https://zhengyang2015.gitbooks.io/lintcode/coins_in_a_line_iii_396.html)

[https://zhengyang2015.gitbooks.io/lintcode/coins\_in\_a\_line\_ii\_395.html](https://zhengyang2015.gitbooks.io/lintcode/coins_in_a_line_ii_395.html)

## 题目描述

```text
There are n coins in a line. Two players take turns to take a coin from one of the ends of the line until there are no more coins left. The payer with the larger amount of money wins.

Could you please decide the first player will win or lose?

Example:
Given array A = [3,2,2], return true.
Given array A = [1,2,4], return true.
Given array A = [1,20,4], return false.
```

## 代码

```java
public class Solution {
    public boolean firstWillWin(int[] values){
    if(values == null || values.length == 0){
      return false;
    }

    if(values.length < 3) {
      return true;
    }

        int n = vlaues.length;
    int[] dp = new int[n];
    dp[n - 1] = values[n - 1];
    dp[n - 2] = values[n - 2] + values[n - 1];
    dp[n - 3] = values[n - 3] + values[n - 2];

    for(int i = n - 4; i >= 0; i--){
      if(i + 4 >= n){
        dp[i] = Math.max(values[n - 4] + dp[n - 1], values[n - 4] + values[n - 3]);
      } else {
        dp[i] = Math.max((values[i] + Math.min(dp[i + 2], dp[i + 3])), 
                         (values[i] + values[i + 1] + Math.min(dp[i + 3], 
                                                               dp[i + 4])));
      }
    }

    int sum = 0;
    for(int i = 0; i < n; i++){
      sum += values[i];
    }

    if(dp[0] > sum - dp[0]){
      return false;
    } else {
      return true;
    }

  }
}
```

