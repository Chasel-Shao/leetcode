## Heapify

----
## 题目地址

[https://www.lintcode.com/problem/heapify](https://www.lintcode.com/problem/heapify)

## 题目描述

```text
Given an integer array, heapify it into a min-heap array.

For a heap array A, A[0] is the root of heap, and for each A[i], A[i * 2 + 1] is the left child of A[i] and A[i * 2 + 2] is the right child of A[i].
```

## 代码

```java
public class Solution {
    public void heapify(int[] nums {
    for (int i = nums.length / 2; i >= 0; i--) {
      minheap(nums, i);
    }
  }

  private void minheap(int[] nums, int k) {
    int n = nums.length;
    while (k < n) {
      int minIndex = k;
      int left = k * 2 + 1;
      int right = k * 2 + 2;
      if (left < n && nums[left] < nums[minIndex]) {
        minIndex = left;
      }
      if (right < n && nums[right] < nums[minIndex]) {
        minIndex = right;
      }

      if (k == minIndex) break;

      int temp = nums[k];
      nums[k] = nums[minIndex];
      nums[minIndex] = temp;
      k = minIndex;
    }
  }

}
```

Approach 2:

```java
public class Solution {

    public void heapify(int nums) {
    for (int i = 0; i < nums.length; i++) {
      siftup(nums, i);
    }
  }

  private void siftup(int[] nums, int k) {
    while (k != 0) {
      int father = (k - 1) / 2;
      if (nums[k] > nums[father]) {
        break;
      }
      int temp = nums[k];
      nums[k] = nums[father];
      nums[father] = temp;

      k = father;
    }
  }

}
```

