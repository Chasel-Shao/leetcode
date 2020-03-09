## Inorder Successor In Binary Search Tree

----
## 题目地址

[http://www.lintcode.com/problem/inorder-successor-in-binary-search-tree/](http://www.lintcode.com/problem/inorder-successor-in-binary-search-tree/)

[https://leetcode.com/problems/inorder-successor-in-bst/solution/](https://leetcode.com/problems/inorder-successor-in-bst/solution/)

## 题目描述

```text
Given a binary search tree (See Definition) and a node in it, find the in-order successor of that node in the BST.

If the given node has no in-order successor in the tree, return null.
```

## 代码

```java
public class Solution {
    public TreeNode inorderSuccessor(TreeNode root, TreeNode p) {
   // the successor is somewhere lower in the right subtree
   // successor: one step right and then left till you can
    if (p.right != null) {
      p = p.right;
      while (p.left != null) p = p.left;
      return p;
    }

    // the successor is somewhere upper in the tree
    ArrayDeque<TreeNode> stack = new ArrayDeque<>();
    int inorder = Integer.MIN_VALUE;

    // inorder traversal : left -> node -> right
    while (!stack.isEmpty() || root != null) {
      // 1. go left till you can
      while (root != null) {
        stack.push(root);
        root = root.left;
      }

      // 2. all logic around the node
      root = stack.pop();
      // if the previous node was equal to p
      // then the current node is its successor
      if (inorder == p.val) return root;
      inorder = root.val;

      // 3. go one step right
      root = root.right;
    }

    // there is no successor
    return null;
  }
}
```

