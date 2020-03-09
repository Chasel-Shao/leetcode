## Sqrt X

----
## 题目地址

[http://www.lintcode.com/problem/sqrtx/description](http://www.lintcode.com/problem/sqrtx/description)

## 题目描述

```text
Implement int sqrt(int x).

Compute and return the square root of x.

Example
Example 1:
    Input:  0
    Output: 0


Example 2:
    Input:  3
    Output: 1

    Explanation:
    return the largest integer y that y*y <= x. 

Example 3:
    Input:  4
    Output: 2
```

mid \* mid == x 中使用乘法可能会溢出，写成 mid == x / mid 即可防止溢出，不需要使用long或者BigInteger

## 代码

```java
public class Solution {
    public int sqrt(int x) {
    if (x < 0) {
      throw new IllegalArgumentException();
    } else if (x <= 1) {
      return x;
    }

    while (start + 1 < end) {
      int mid = start + (end - start) / 2;
      if (mid == x / mid) {
        return mid;
      } else if (mid < x / mid) {
        start = mid;
      } else {
        end = mid;
      }
    }

    if ( end > x / end) {
      return start;
    } else {
      return end;
    }

  }
}
```

Appraoch 2: 牛顿迭代法

牛顿迭代法。令t = sqrt\(x\), 根据 x = sqrt\(x\) \* sqrt\(x\)构造不动点

n = t  _t n + t_  t = 2  _t_  t \(n / t\) + t = 2 \* t t = \(n / t + t\) / 2

```java
class Solution {
  public int mySqrt(int x) {
    return (int)sqrt(x);
  }

  private double sqrt(int n) {
    double guess = 1.0;
    while (Math.abs(n - guess * guess) > 0.1) {
      guess = ( n / guess + guess ) / 2;
    }
    return guess;
  }

}
```

Appraoch 3:

```java
class Solution {
  public int mySqrt(int x) {
    long X = (long) x;
    long l = 1, r = X;

    while (l + 1 < r) {
      long mid = l + (r - l) / 2;
      if ( mid * mid == X ) {
        return (int) mid;
      } else if (mid * mid < X) {
        l = mid;
      } else {
        r = mid;
      }
    }

    if (r * r == X) return (int) r;
    return (int) l;
  }
}
```

