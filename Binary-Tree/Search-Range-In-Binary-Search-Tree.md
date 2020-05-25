## Search Range In Binary Search Tree

----
## 题目地址

[https://www.lintcode.com/problem/search-range-in-binary-search-tree/description](https://www.lintcode.com/problem/search-range-in-binary-search-tree/description)

[https://www.jiuzhang.com/solution/search-range-in-binary-search-tree/](https://www.jiuzhang.com/solution/search-range-in-binary-search-tree/)

## 题目描述

```text
Given a binary search tree and a range [k1, k2], return node values within a given range in ascending order.
```

## 代码

```java
public class Solution {
  private ArrayList<Integer> results;

  public ArrayList<Integer> searchRange(TreeNode root, int k1, int k2) {
    results = new ArrayList<Integer>();
    helper(root, k1, k2);
    return results;
  }

  private void helper(TreeNode root, int k1, int k2) {
    if (root == null) return;

    if (root.val > k1) {
      helper(root.left, k1, k2);
    }

    if (root.val >= k1 && root.val <= k2) {
      results.add(root.val);
    }

    if (root.val < k2) {
      helper(root.right, k1, k2);
    }
  }

}
```

