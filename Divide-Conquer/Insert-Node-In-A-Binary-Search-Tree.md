## Insert Node In A Binary Search Tree

----
## 题目地址

[https://www.lintcode.com/problem/insert-node-in-a-binary-search-tree/description](https://www.lintcode.com/problem/insert-node-in-a-binary-search-tree/description)

[https://www.jiuzhang.com/solution/insert-node-in-a-binary-search-tree/](https://www.jiuzhang.com/solution/insert-node-in-a-binary-search-tree/)

## 题目描述

```text
Given a binary search tree and a new tree node, insert the node into the tree. You should keep the tree still be a valid binary search tree.
```

## 代码

### Approach #1 Recursion

```java
public class Solution {
    public TreeNode insertNode(TreeNode root, TreeNode node) {
    if (root == null) return node;

    if (root.val > node.val) {
      root.left = insertNode(root.left, node);
    } else {
      root.right = insertNode(root.right, node);
    }

    return root;
  }

}
```













