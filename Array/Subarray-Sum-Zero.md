## Subarray Sum Zero

----
## 题目地址

[https://www.lintcode.com/problem/subarray-sum/description](https://www.lintcode.com/problem/subarray-sum/description)

## 题目描述

```text
Given an integer array, find a subarray where the sum of numbers is zero. Your code should return the index of the first number and the index of the last number.
```

## 代码

```java
public class Solution {
  public ArrayList<Integer> subarraySum (int[] nums) {
    ArrayList<Integer> result = new ArrayList<Integer>();
    Map<Integer, Integer> hashMap = new HashMap<Integer, Integer>();
    int sum = 0;
    for (int i = 0; i < nums.length; i++) {
      sum += nums[i];
      if (sum == 0) {
        result.add(0);
        result.add(i);
        return result;
      }

      if (hashMap.containsKey(sum)) {
        int index = hashMap.get(sum);
        result.add(index);
        result.add(i);
        return result;
      }

      hashMap.put(sum, i);
    }

    return result;
  }
}
```

