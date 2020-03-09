## Max Depth Of Binary Tree

----
## 题目地址

[https://leetcode.com/problems/maximum-depth-of-binary-tree](https://leetcode.com/problems/maximum-depth-of-binary-tree)

[http://www.lintcode.com/problem/maximum-depth-of-binary-tree/](http://www.lintcode.com/problem/maximum-depth-of-binary-tree/)

[http://www.jiuzhang.com/solutions/maximum-depth-of-binary-tree/](http://www.jiuzhang.com/solutions/maximum-depth-of-binary-tree/)

## 题目描述

```text
Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.
```

## 代码

Approach 1: Divide Conquer \(Recursive\)

**Intuition** By definition, the maximum depth of a binary tree is the maximum number of steps to reach a leaf node from the root node.

**Complexity analysis**

* Time complexity : we visit each node exactly once, thus the time complexity is O\(_N_\), where _N_ is the number of nodes.
* Space complexity : in the worst case, the tree is completely unbalanced, _e.g._ each node has only left child node, the recursion call would occur _N_ times \(the height of the tree\), therefore the storage to keep the call stack would be O\(_N_\). But in the best case \(the tree is completely balanced\), the height of the tree would be log\(_N_\). Therefore, the space complexity in this case would be O\(log\(_N_\)\).

```java
public class Solution {
    public int maxDepth(TreeNode root) {
    if (root == null) return 0;
  }

  int left = maxDepth(root.left);
  int right = maxDepth(root.right);
  return Math.max(left, right) + 1;
}
```

Approach 2: Traverse

```java
class Solution {
  private int depth;

  public int maxDepth(TreeNode root) {
    depth = 0;
    helper(root, 1);

    return depth;
  }

  private void helper(TreeNode node, int curtDepth) {
    if (node == null) return;

    if (curtDepth > depth) {
      depth = curtDepth;
    }

    helper(node.left, curtDepth + 1);
    helper(node.right, curtDepth + 1);
  }
}
```

Approach 3: Iteration

```java
class Solution {
  public int maxDepth(TreeNode root) {
    LinkedList<TreeNode> stack = new LinkedList<>();
    LinkedList<TreeNode> depths = new LinkedList<>();
    if (root == null)    return 0;

    stack.add(root);
    depths.add(1);

    int depth = 0;
    int current_depth = 0;
    while (!stack.isEmpty()) {
      root = stack.pollLast();
      current_depth = depths.pollLast();
      if (root != null) {
        depth = Math.max(depth, current_depth);
        stack.add(root.left);
        stack.add(root.right);
        depths.add(current_depth + 1);
        depths.add(current_depth + 1);
      }
    }

    return depth;
  }
}
```

