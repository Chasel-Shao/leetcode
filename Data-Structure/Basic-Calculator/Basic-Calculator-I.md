## Basic Calculator I

----
## 题目地址

[https://leetcode.com/problems/basic-calculator/description/](https://leetcode.com/problems/basic-calculator/description/)

## 题目描述

```text
Implement a basic calculator to evaluate a simple expression string.

The expression string may contain open ( and closing parentheses ), the plus + or minus sign -, non-negative integers and empty spaces .

Example 1:

Input: "1 + 1"
Output: 2
Example 2:

Input: " 2-1 + 2 "
Output: 3
Example 3:

Input: "(1+(4+5+2)-3)+(6+8)"
Output: 23

Note:
You may assume that the given expression is always valid.
Do not use the eval built-in library function.
```

## 代码

Approach 1:

```java
class Solution {
    public int calculate(String s) {
      int len = s.length(), sign = 1, result = 0;
    Stack<Integer> stack = new Stack<Integer>();
    for (int i = 0; i < len; i++) {
      if (Character.isDigit(s.charAt(i))) {
        int num = s.charAt(i) - '0';
        while (i + 1 < len && Character.isDigit(s.charAt(i + 1))) {
          num = num * 10 + s.charAt(i + 1) - '0';
          i++;
        }
        result += num * sign;
      } else if (s.charAt(i) == '+') {
        sign = 1;
      } else if (s.charAt(i) == '-') {
        sign = -1;
      } else if (s.charAt(i) == '(') {
        stack.push(result);
        stack.push(sign);
        result = 0;
        sign = 1;
      } else if (s.charAt(i) == ')') {
        result = result * stack.pop() + stack.pop();
      }
    }

    return result;
    }
}
```

Approach \#2 Stack and No String Reversal

```java
class Solution {
    public int calculate(String s) {
        Stack<Integer> stack = new Stack<Integer>();
        int operand = 0;
        int result = 0;
        int sign = 1;

        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            if (Character.isDigit(ch)) {
                operand = (int)(ch - '0');
                 while (i + 1 < s.length() && Character.isDigit(s.charAt(i + 1))) {
                    operand = operand * 10 + s.charAt(i + 1) - '0';
                    i++;
                }

                result = result + sign * operand;
            } else if (ch == '+') {
                sign = 1;
                operand = 0;

            } else if (ch =='-') {
                sign = -1;
                operand = 0;

            } else if (ch == '(') {

                stack.push(result);
                stack.push(sign);

                sign = 1;
                result = 0;

            } else if (ch == ')') {
                // pop sign
                result *= stack.pop();
                // pop last result
                result += stack.pop();

                operand = 0;
            }
        }

        return result;
    }
}
```

