## Capacity To Ship Packages

----
## 题目地址

[https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/)

## 题目描述

```text
A conveyor belt has packages that must be shipped from one port to another within D days.

The i-th package on the conveyor belt has a weight of weights[i].  Each day, we load the ship with packages on the conveyor belt (in the order given by weights). We may not load more weight than the maximum weight capacity of the ship.

Return the least weight capacity of the ship that will result in all the packages on the conveyor belt being shipped within D days.

Example 1:
Input: weights = [1,2,3,4,5,6,7,8,9,10], D = 5
Output: 15
Explanation: 
A ship capacity of 15 is the minimum to ship all the packages in 5 days like this:
1st day: 1, 2, 3, 4, 5
2nd day: 6, 7
3rd day: 8
4th day: 9
5th day: 10

Note that the cargo must be shipped in the order given, so using a ship of capacity 14 and splitting the packages into parts like (2, 3, 4, 5), (1, 6, 7), (8), (9), (10) is not allowed. 

Example 2:
Input: weights = [3,2,2,4,1,4], D = 3
Output: 6
Explanation: 
A ship capacity of 6 is the minimum to ship all the packages in 3 days like this:
1st day: 3, 2
2nd day: 2, 4
3rd day: 1, 4

Example 3:
Input: weights = [1,2,3,1,1], D = 4
Output: 3
Explanation: 
1st day: 1
2nd day: 2
3rd day: 3
4th day: 1, 1

Note:
1 <= D <= weights.length <= 50000
1 <= weights[i] <= 500
```

## 代码

Approach 1: Binary Search

The `left` bound is `max(A)`, The `right` bound is `sum(A)`.

```java
class Solution {
    public int shipWithinDays(int[] weights, int D) {
    int left = 0, right = 0;
    for (int w: weights) {
      left = Math.max(left, w);
      right += w;
    }

    while (left < right) {
      // Take the maximum weight that only needs two ships
      int mid = (left + right) / 2;
      int need = 1, cur = 0;
      // Calculate the number of ships required
      for (int w : weights) {
        if (cur + w > mid) {
          need += 1;
          cur = 0;
        }
        cur += w;
      }

      if (need > D) {
        left = mid + 1;
      } else {
        right = mid;
      }
    }

    return left;
  }
}
```

### More Good Binary Search Problems

Here are some similar binary search problems. Also find more explanations. Good luck and have fun.

* [Find the Smallest Divisor Given a Threshold](https://leetcode.com/problems/find-the-smallest-divisor-given-a-threshold/discuss/446376/javacpython-bianry-search/401806)
* [Divide Chocolate](https://leetcode.com/problems/divide-chocolate/discuss/408503/Python-Binary-Search)
* [Capacity To Ship Packages In N Days](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/discuss/256729/javacpython-binary-search/351188?page=3)
* [Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/discuss/152324/C++JavaPython-Binary-Search)
* [Minimize Max Distance to Gas Station](https://leetcode.com/problems/minimize-max-distance-to-gas-station/discuss/113633/Easy-and-Concise-Solution-using-Binary-Search-C++JavaPython)
* [Split Array Largest Sum](https://leetcode.com/problems/split-array-largest-sum/)

