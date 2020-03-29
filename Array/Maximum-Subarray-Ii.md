## Maximum Subarray Ii

----
## 题目地址

[https://www.lintcode.com/problem/maximum-subarray-ii/description](https://www.lintcode.com/problem/maximum-subarray-ii/description)

## 题目描述

```text
Given an array of integers, find two non-overlapping subarrays which have the largest sum.
The number in each subarray should be contiguous.
Return the largest sum.
```

## 代码

```java
public class Solution {
  public int maxTwoSubArray(ArrayList<Integer> nums) {
    if (nums == null || nums.isEmpty()) return -1;
    int size = nums.size();
    int[] maxSubArrayFront = new int[size];
    forwardTraversal(nums, maxSubArrayFront);

    int[] maxSubArrayBack = new int[size];
    backwardTraversal(nums, maxSubArrayBack);

    int maxTwoSub = Integer.MIN_VALUE;
    for (int i = 0; i < size - 1; i++) {
      maxTwoSub = Math.max(maxTwoSub, maxSubArrayFront[i] + maxSubArrayBack[i + 1]);
    }

    return maxTwoSub;
  }

  private void forwardTraversal(List<Integer> nums, int[] maxSubArray) {
    int sum = 0, minSum = 0, maxSub = Integer.MIN_VALUE;
    int size = nums.size();
    for (int i = 0; i < size; i++) {
      minSum = Math.min(minSum, sum);
      sum += nums.get(i);
      maxSub = Math.max(maxSub, sum - minSum);
      maxSubArray[i] = maxSub;
    }
  }

  private void backwardTraversal(List<Integer> nums, int[] maxSubArray) {
    int sum = 0, minSum = 0, maxSub = Integer.MIN_VALUE;
    int size = nums.size();
    for (int i = size - 1; i >= 0; i--) {
      minSum = Math.min(minSum, sum);
      sum += nums.get(i);
      maxSub = Math.max(maxSub, sum - minSum);
      maxSubArray[i] = maxSub;
    }
  }

}
```

