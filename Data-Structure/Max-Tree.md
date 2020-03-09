## Max Tree

----
## 题目地址

[https://leetcode.com/problems/maximum-binary-tree/](https://leetcode.com/problems/maximum-binary-tree/)

## 题目描述

```text
Given an integer array with no duplicates. A maximum tree building on this array is defined as follow:

The root is the maximum number in the array.
The left subtree is the maximum tree constructed from left part subarray divided by the maximum number.
The right subtree is the maximum tree constructed from right part subarray divided by the maximum number.
Construct the maximum tree by the given array and output the root node of this tree.
```

## 代码

Approach 1: Recursive Solution

```java
public class Solution {
  public TreeNode constructMaximumBinaryTree(int nums) {
    return construct(nums, 0, nums.length);
  }

  public TreeNode construct(int[] nums, int l, int r) {
    if (l == r) return null;
    int maxIndex = Math.max(nums, l, r);
    TreeNode root = new TreeNoe(nums[maxIndex]);
    root.left = construct(nums, l, maxIndex)；
    root.right = construct(nums, maxIndex + 1, r);
    return root;
  }

  public int max(int[] nums, int l, int r) {
    int maxIndex = 1;
    for (int i = 1; i < r; i++) {
      if (nums[maxIndex] < nums[i]) {
        maxIndex = i;
      }
    }
    return maxIndex;
  }

}
```

Approach 2: Use Monotone decreasing stack

```java
public class Solution {
class TreeNode {
        int val;
        TreeNode left;
        TreeNode right;
        TreeNode(int val) {
            this.val = val;
        }
    }

    public int maxTree(int[] arr) {
        Stack<TreeNode> stack = new Stack<TreeNode>();
        for (int e : arr) {
            TreeNode node = new TreeNode(e);
            while (!stack.isEmpty() && e > stack.peek().val) {
                node.left = stack.pop();
            }
            if (!stack.isEmpty()) {
                stack.peek().right = node;
            }

            stack.push(node);
        }

        return stack.firstElement().val;
    }
}
```

