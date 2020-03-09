## Subarray Sum Zero

----
## 题目地址

[https://www.lintcode.com/problem/subarray-sum](https://www.lintcode.com/problem/subarray-sum)

[https://leetcode.com/problems/continuous-subarray-sum/](https://leetcode.com/problems/continuous-subarray-sum/)

## 题目描述

```text
Given an integer array, find a subarray where the sum of numbers is zero. Your code should return the index of the first number and the index of the last number.
```

## 代码

```java
public class Solution {
    int n = nums.length;
  ArrayList<Integer> result = new ArrayList<Integer>();
  HashMap<Integer, Integer> map = new HashMap<>();
  map.put(0, -1);
  int sum = 0;
  for (int i = 0; i < n; i++) {
    sum += nums[i];
    if (map.containsKey(sum)) {
      result.add(map.get(sum) + 1);
      result.add(i);
      return result;
    }
    map.put(sum, i);
  }

  return result;
}
```

Approach 2:

```java
public class Solution {
  public int maxSubArray(int[] nums) {
    if (nums == null || nums.isEmpty()) return -1;
    ArrayList<Integer> result = new ArrayList<Integer>();
      HashMap<Integer, Integer> map = new HashMap<>();
    int sum = 0, minSum = 0, maxSub = Integer.MIN_VALUE;
    for (int i = 0; i < n; i++) {
      minSum = Math.min(minSum, sum);
      sum += nums[i];
      if (maxSub < sum - minSum) {
        maxSub = sum - minSum;
        map.put(sum, i);
        result.
      }
    }
  }
}
```

