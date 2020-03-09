## Backpack Iii

----
## 题目地址

[https://www.lintcode.com/problem/backpack-iii/description](https://www.lintcode.com/problem/backpack-iii/description)

## 题目描述

```text
Given n kind of items with size Ai and value Vi( each item has an infinite number available) and a backpack with size m. What's the maximum value can you put into the backpack?
```

## 代码

```java
public class Solution {
    public int backpack (int m, int[] A, int[] V, int[] num) {
    if (A == null || A.length < 0) {
        return 0;
    }
       int[][] f = new int[A.length + 1][m + 1];
    for (int i = 1; i < A.length; i++) {
      for (int j = 0; i <= m; j++) {
        if (j >= A[i]) {
          int maxV = Math.min(num[i - 1], j / A[i - 1]);
          for (int k = 0; k < maxV + 1; k ++) {
              f[i][j] = Math.max(f[i - 1][j], f[i - 1][j - k * A[i] + k * V[i]);
          }
        } else {
          f[i][j] = f[i - 1][j];
        }
      }
    }
    return f[A.length][m];
  }
}
```

