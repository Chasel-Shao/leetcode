## Implement Queue By Two Stacks

----
## 题目地址

[https://www.lintcode.com/problem/implement-queue-by-two-stack](https://www.lintcode.com/problem/implement-queue-by-two-stack)

## 题目描述

```text
As the title described, you should only use two stacks to implement a queue's actions.

The queue should support push(element), pop() and top() where pop is pop the first(a.k.a front) element in the queue.

Both pop and top methods should return the value of first element.
```

## 代码

```java
public class Solution {
    private Stack<Integer> stack1;
  private Stack<Integer> stack2;

  public Solution() {
    stack1 = new Stack<Integer>();
    stack2 = new Stack<Integer>();
  }

  public void push(int element) {
    stack1.push(element);
  }

  public int pop() {
    if (stack2.empty()) {
      stack1ToStack2(stack1, stack2);
    }
    return stack2.pop();
  }

  public int top() {
    if (stack2.empty()) {
      stack1ToStack2(stack1, stack2);
    }
    return stack2.peek();
  }

  private void stack1ToStack2() {
    while (!stack1.empty()) {
      stack2.push(stack1.pop());
    }
  }

}
```

