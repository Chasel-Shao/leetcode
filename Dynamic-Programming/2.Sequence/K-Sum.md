## K Sum

----
## 题目地址

[https://www.lintcode.com/problem/k-sum/description](https://www.lintcode.com/problem/k-sum/description)

## 题目描述

```text
Given n distinct postive integers, integer k (k <= n) and a number target.

Find k numbers where sum is target. Calculate how many solutions there are?
```

## 代码

### Approach #1 Dynamic Programming

`用dp[i][j][t]表示前i个数里选j个和为target的方案数`

```java
public class Solution {
    public int kSum(int A[], int k, int target) {
      if (A == null || A.length == 0)  return 0;
      
      int n = A.length;
      int[][][] dp = new int[n + 1][k + 1][target + 1];

      for (int i = 0; i <= n; i++){
        dp[i][0][0] = 1;
      }

      for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= k && j <= i; j++) {
          for (int t = 1; t <= target; t++) {
            if (t >= A[i - 1]) {
              dp[i][j][t] = dp[i - 1][j][t] + dp[i - 1][j - 1][t - A[i - 1]];
            } else {
              dp[i][j][t] = dp[i - 1][j][t];
            }
          }
        }
      }
    	return dp[n][k][target];
  }
}
```

### Approach #2 

```java
public class Solution {
  int len = 0;
  public List<List<Integer>> fourSum(int[] nums, int k, int target) {
    len = nums.length;
    Arrays.sort(nums);
    return kSum(nums, target, k, 0);
  }
  
  private ArrayList<List<Integer>> kSum(int[] nums, int target, int k, int index) {
    ArrayList<List<Integer>> res = new ArrayList<List<Integer>>();
    if (index >= len) {
        return res;
    }
    if (k == 2) {
      int i = index, j = len - 1;
      while (i < j) {
         // find a pair
        if (target - nums[i] == nums[j]) {
        	List<Integer> temp = new ArrayList<>();
          temp.add(nums[i]);
          temp.add(target - nums[i]);
          res.add(temp);
          // skip duplication
          while (i < j && nums[i] == nums[i+1]) i++;
          while (i < j && nums[j-1] == nums[j]) j--;
          i++;
          j--;
          // move left bound
        } else if (target - nums[i] > nums[j]) {
          i++;
          // move right bound
        } else {
          j--;
        }
      }
    } else {
      for (int i = index; i < len - k + 1; i++) {
        //use current number to reduce ksum into k-1 sum
        ArrayList<List<Integer>> temp = kSum(nums, target - nums[i], k-1, i+1);
        if (temp != null) {
          //add previous results
          for (List<Integer> t: temp) {
          	t.add(0, nums[i]);
          }
          res.addAll(temp);
        }
        while (i < len-1 && nums[i] == nums[i+1]) {
            //skip duplicated numbers
        	i++;
        }
      }
    }
    return res;
  }
}
```

