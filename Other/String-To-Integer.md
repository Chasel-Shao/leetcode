## String To Integer

----
## 题目地址

* leetcode: [String to Integer \(atoi\) \| LeetCode OJ](https://leetcode.com/problems/string-to-integer-atoi/)
* lintcode: [\(54\) String to Integer\(atoi\)](http://www.lintcode.com/en/problem/string-to-integer-ii/)

## 题目描述

```text
Implement function atoi to convert a string to an integer.

If no valid conversion could be performed, a zero value is returned.

If the correct value is out of the range of representable values,
INT_MAX (2147483647) or INT_MIN (-2147483648) is returned.

Example
"10" => 10

"-1" => -1

"123123123123123" => 2147483647

"1.0" => 1
```

## 解题思路

边界条件：

1. 字符串是否为空
2. 左右空白字符
3. 数字的符号
4. 非法字符
5. Overflow

## 代码

```java
public class Solution {
    public int atoi（String str) {
    if (str == null || str.length() == 0) return 0;

       String strTrim = str.trim();
    int len = strTrim.length();
    int sign = 1;
    int i = 0;
    if (strTrim.charAt(i) == '+') {
      i++;
    } else if (strTrim.charAt(i) == '-') {
      sign = -1;
      i++;
    }

    long result = 0;
    while (i < len) {
      if (strTrim.charAt(i) < '0' || strTrim.charAt(i) > '9') {
        break;
      }

      result = 10 * result + sign * (strTrim.charAt(i) - '0');

      if (result > Integer.MAX_VALUE) {
        return Integer.MAX_VALUE;
      } else if (result < Integer.MIN_VALUE) {
        return Integer.MIN_VALUE;
      }
      i++;
    }

    return (int)result;
  }

}
```

