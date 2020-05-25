## Preorder

----
## 题目地址

* [http://www.lintcode.com/problem/binary-tree-preorder-traversal/](http://www.lintcode.com/problem/binary-tree-preorder-traversal/)
* [http://www.jiuzhang.com/solutions/binary-tree-preorder-traversal/](http://www.jiuzhang.com/solutions/binary-tree-preorder-traversal/)

## 题目描述

```text
Given a binary tree, return the preorder traversal of its nodes' values.

The first data is the root node, followed by the value of the left and right son nodes, and "#" indicates that there is no child node.
The number of nodes does not exceed 20.
```

## 代码

### Approach #1 No-Recursion

```java
public class Solution {
    public List<Integer> preorderTraverl(TreeNode root) {
    Stack<TreeNode> stack = new Stack<TreeNode>();
    List<IInteger> preorder = new ArrayList<Interger>();

    if (root == null) {
      return preorder;
    }

    stack.push(root);
    while (!stack.empty()) {
      TreeNode node = stack.pop();
      preorder.add(node.val);
      if (node.right != null) {
        stack.push(node.right);
      }
      if (node.left != null) {
        stack.push(node.left);
      }
    }

    return preorder;
  }

}
```

### Approach #2 Traverse

```java
class Solution {
  public ArrayList<Integer> preorderTraversal(TreeNode root) {
    ArrayList<Integer> result = new ArrayList<Integer>();
    traverse(root, result);
    return results;
  }

  private void traverse(TreeNode root, ArrayList<Integer> result) {
    if (root == null) return;

    result.add(root.val);
    travese(root.left, result);
    travese(root.right, result);
  }
}
```

### Approach #3 Divide & Conquer

```java
class Solution {
  public ArrayList<Integer> preorderTraversal(TreeNode root) {
    ArrayList<Integer> result = new ArrayList<Integer>();
    if (root == null) return result;

    // Divide
    ArrayList<Integer> left = preorderTraversal(root.left);
    ArrayList<Integer> right = preorderTraversal(root.right);

    // Conquer
    result.add(root,val);
    result.addAll(left);
    result.addAll(right);
    return result;
  }
}
```

