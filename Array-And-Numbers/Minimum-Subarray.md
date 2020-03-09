## Minimum Subarray

----
## 题目地址

[https://www.lintcode.com/problem/minimum-subarray/description](https://www.lintcode.com/problem/minimum-subarray/description)

## 题目描述

```text
Given an array of integers, find the continuous subarray with smallest sum.

Return the sum of the subarray.
```

## 代码

```java
public class Solution {
    public int minSubArray(ArrayList<Integer> nums) {
   if (nums == null || nums.isEmpty()) return -1;
    int sum = 0, maxSum = 0, minSub = Integer.MAX_VALUE;
    for (int num : nums) {
      maxSum = Math.max(maxSum, sum);
      sum += num;
      minSub = Math.min(minSub, sum - maxSum);
    }

    return minSub;
  }
}
```

Solution 2:

```java
public class Solution {
  public int minSubArray(ArrayList<Integer> nums) {
    if (nums == null || nums.isEmpty()) return -1;
    int[] copys = new int[nums.size()];
    for (int i = 0; i < nums.size(); i++){
      copys[i] = -1 * nums[i];
    }

    int sum = 0, maxSum = Integer.MIN_VALUE;
    for (int num : copys){
      sum = Math.max(sum, 0);
      sum += num;
      maxSum = Math.max(maxSum, sum);
    }

    return maxSum * -1;
  }
}
```

