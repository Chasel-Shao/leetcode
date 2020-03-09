## Count Of Smaller Number

----
## 题目地址

[http://www.lintcode.com/problem/count-of-smaller-number/description](http://www.lintcode.com/problem/count-of-smaller-number/description)

## 题目描述

```text
Give you an integer array (index from 0 to n-1, where n is the size of this array, value from 0 to 10000) and an query list. For each query, give you an integer, return the number of element in the array that are smaller than the given integer.

Example
Example 1:

Input: array =[1,2,7,8,5] queries =[1,8,5]
Output:[0,4,2]
Example 2:

Input: array =[3,4,5,8] queries =[2,4]
Output:[0,1]
Challenge
Could you use three ways to do it.

Just loop
Sort and binary search
Build Segment Tree and Search.
```

## 代码

```java
public class Solution {

  class SegmentTreeNode {
    public int start, end;
    public int count;
    public SegmentTreeNode left, right;
    public SegmentTreeNode(int start, int end, int count) {
      this.start = start;
      this.end = end;
      this.count = count;
      this.left = this.right = null;
    }
  }

  SegmentTreeNode root;
  public SegmentTreeNode build(int start, int end) {
    if (start > end) return null;

    SegmentTreeNode root = new SegmentTreeNode(start, end, 0);

    if (start != end) {
      int mid = (start + end) / 2;
      root.left = build(start, mid);
      root.right = build(mid + 1, end);
    } else {
      root.count = 0;
    }
    return root;
  }

  public int querySegmentTree(SegmentTreeNode root, int start, int end) {
    if (start == root.start && root.end == end) return root.count;

    int mid = (root.start + root.end) / 2;
    int leftCount = 0, rightCount = 0;

    if (start <= mid) {
      if (mid < end) {
        leftCount = querySegmentTree(root.left, start, mid);
      } else {
        leftCount = querySegmentTree(root.left, start, end);
      }
    }

    if (mid < end) {
      if (start <= mid) {
        rightCount = querySegmentTree(root.right, mid + 1, end);
      } else {
        rightCount = querySegemntTree(root.right, start, end);
      }
    }

    return leftCount + rightCount;
  }

  public void modifySegmentTree(SegmentTreeNode root, int index, int value) {
    if (root.start == index && root.end == index) {
      root.count += value;
      return;
    }

    int mid = (root.start + root.end) / 2;
    if (root.start <= index && index <= mid) {
      modifySegemntTree(root.left, index. vlaue);
    }

    if (mid < index && index <= root.end) {
      modifySegmentTree(root.right, index, value);
    }

    root.count = root.left.count + root.right.count;
  }

  public ArrayList<Integer> countOfSmallerNumber(int[] A, int[] queries) {
    root = build(0, 10000);
    ArrayList<Integer> ans = new ArrayList<Integer>();
    int res;
    for (int i = 0; i < A.length; i++) {
      modifySegmentTree(root, A[i], 1);
    }
    for (int i = 0; i < queries.length; i++) {
      res = 0;
      if (queries[i] > 0) {
        res = querySegmentTree(root, 0, queries[i] - 1);
      }
      ans.add(res);
    }
    return ans;
  }

}
```

