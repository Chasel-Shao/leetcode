## Postorder

----
## 题目地址

* [http://www.lintcode.com/en/problem/binary-tree-postorder-traversal/](http://www.lintcode.com/en/problem/binary-tree-postorder-traversal/)
* [http://www.jiuzhang.com/solutions/binary-tree-postorder-traversal/](http://www.jiuzhang.com/solutions/binary-tree-postorder-traversal/)

## 题目描述

```text
Given a binary tree, return the postorder traversal of its nodes' values.
```

## 代码

### Approach 1: Recursive

```java
public class Solution {
    public ArrayList<Integer> postorderTraversal(TreeNode root) {
    ArrayList<Integer> result = new ArrayList<Integer>();
    if (root == null) return result;

    result.addAll(postorderTraversal(root.left));
    result.addAll(postorderTraversal(root.right));
    result.add(root.val);

    return result;
  }

  public ArrayList<Integer> postorderTraversal(TreeNode root) {
    ArrayList<Integer> result = new ArrayList<Integer>();
    if (root == null) return result;

    Stack<TreeNode> stack = new Stack<TreeNode>();
    TreeNode prev = null;
    TreeNode curr = root;

    stack.push(root);
    while (!stack.empty()) {
      curr = stack.peek();
      if (prev == null || prev.left == curr || prev.right == curr) {
        if (curr.left != null) {
          stack.push(curr.left);
        } else if (curr.right != null) {
          stack.push(curr.right);
        }
      } else if (curr.left == prev) {
        if (curr.right != null) {
          stack.push(curr.right);
        }
      } else {
        result.add(curr.val);
        stack.pop();
      }
      prev = curr;
    }

    return result;
  }
}
```

### Approach #2

```java
public ArrayList<Integer> postorderTraversal(TreeNode root) {
  ArrayList<Integer> result = new ArrayList<>();
  Stack<TreeNode> stack = new Stack<>();
  stack.push(root);
  while (!stack.isEmpty()) {
    TreeNode node = stack.pop();
    result.add(0, node.val);
    if (node.left != null) 		stack.push(node.left);
    if (node.right != null) 	stack.push(node.right);
  }
    return result;
}
```

