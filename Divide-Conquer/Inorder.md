## Inorder

----
## 题目地址

* [http://www.lintcode.com/en/problem/binary-tree-inorder-traversal/](http://www.lintcode.com/en/problem/binary-tree-inorder-traversal/)
* [http://www.jiuzhang.com/solutions/binary-tree-inorder-traversal/](http://www.jiuzhang.com/solutions/binary-tree-inorder-traversal/)

## 题目描述

```text
Given a binary tree, return the inorder traversal of its nodes' values.
```

## 代码

### Approach 1: Stack + Two while-loop

```java
public class Solution {
    public ArrayList<Integer> inorderTraversal(TreeNode root) {
    Stack<TreeNode> stack = new Stack<>();
    ArrayList<Integer> result = new ArrayList<>();
		// 1.
    while (root != null) {
      stack.push(root);
      root = root.left;
    }
 		// 2.
    while (!stack.empty()) {
      TreeNode node = stack.peek();
      result.add(node.val);

      if (node.right == null) {
        node = stack.pop();
        while (!stack.isEmpty() && stack.peek().right == node) {
          node = stack.pop();
        }
      } else {
        node = node.right;
        while (node != null) {
          stack.push(node);
          node = node.left;
        }
      }

    }

    return result;
  }

}
```

### Approach 2: Stack

```java
class Solution {
  public ArrayList<Integer> inorderTraversal(TreeNode root) {
    Stack<TreeNode> stack = new Stack<TreeNode>();
    ArrayList<Integer> result = new ArrayList<Integer>();
    TreeNode curt = root;
    while (!stack.empty() || curt != null) {
      while (curt != null) {
        stack.add(curt);
        curt = curt.left;
      }
      curt = stack.pop();
      result.add(curt.val);
      curt = curt.right;
    }
    return result;
  }
}
```

