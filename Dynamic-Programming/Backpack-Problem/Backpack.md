## Backpack

----
## 题目地址

https://www.lintcode.com/problem/backpack

## 题目描述

```text
Given n items with size Ai, an integer m denotes the size of a backpack. How full you can fill this backpack?

Example
Example 1:
	Input:  [3,4,8,5], backpack size=10
	Output:  9

Example 2:
	Input:  [2,3,5,7], backpack size=12
	Output:  12
	
Challenge
O(n x m) time and O(m) memory.

O(n x m) memory is also acceptable if you do not know how to optimize memory.
```

## 代码

```java
public class Solution {
    public int backpack (int m, int[] A) {
    if (A == null || A.length < 0) {
        return 0;
    }
       int[] f = new int[m + 1];
    for (int i = 0; i < A.length; i++) {
      for (int j = m; i > 0; j--) {
        if (j >= A[i]) {
          f[j] = Math.max(f[j], f[j - A[i]] + A[i]);
        }
      }
    }
    return f[m];
  }
}
```

```java
public class Solution {
    public int backpack (int m, int[] A) {
    if (A == null || A.length < 0) {
        return 0;
    }
       int[][] f = new int[A.length + 1][m + 1];
    for (int i = 1; i < A.length; i++) {
      for (int j = 0; i <= m; j++) {
        if (j >= A[i]) {
          f[i][j] = Math.max(f[i - 1][j], f[i - 1][j - A[i] + A[i]);
        } else {
          f[i][j] = f[i - 1][j];
        }
      }
    }
    return f[A.length][m];
  }
}
```

