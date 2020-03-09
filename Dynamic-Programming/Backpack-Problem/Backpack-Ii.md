## Backpack Ii

----
## 题目地址

[https://www.lintcode.com/problem/backpack-ii/description](https://www.lintcode.com/problem/backpack-ii/description)

## 题目描述

```text
There are n itmes and a backpack with size m. Given array A representing the size of each item and array V representing the value of each item.

What's the maximum value can you put into the backpack?
```

## 代码

```java
public class Solution {
    public int backpack(int m, int[] A, int[] V) {
    if (A == null || A.length == 0 || V == null || V.length == 0) {
        return 0;
    }
       int[] f = new int[m + 1];
    for (int i = 0; i < A.length; i++) {
      for (int j = m; i > 0; j--) {
        if (j >= A[i]) {
          f[j] = Math.max(f[j], f[j - A[i]] + V[i]);
        }
      }
    }
    return f[m];
  }
}
```

