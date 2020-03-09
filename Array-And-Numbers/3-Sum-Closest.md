## 3 Sum Closest

----
## 题目地址

[https://www.lintcode.com/en/problem/3-sum-closest/](https://www.lintcode.com/en/problem/3-sum-closest/)

## 题目描述

```text
Given an array S of n integers, find three integers in S such that the sum is closest to a given number, target. 
Return the sum of the three integers. You may assume that each input would have exactly one solution.

For example, given array S = {-1 2 1 -4}, and target = 1.
The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
```

## 代码

```java
public class Solution {
    public int threeSumClosest(int[] nums, int target) {
    if (num.length <= 3) {
      int sum = 0;
      for (int num : nums) {
        sum += num;
      }
      return sum;
    }

    Arrays.sort(nums);
    int n = nums.length;
    int result = nums[0] + nums[1] + nums[2];
    for (int i = 0; i < n - 2; ++i) {
      int start = i + 1;
      int end = n - 1;
      while (start < end) {
       int temp = nums[i] + nums[start] + nums[end];
        if (abs(target - temp) < abs(target - result)) {
          result = temp;
        } 

        if (result == target) return result;

        if (temp > target) {
          --end;
        } else {
          ++start;
        }

      }
    }
    return result;
  }
}
```

