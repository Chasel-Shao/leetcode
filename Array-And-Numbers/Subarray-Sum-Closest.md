## Subarray Sum Closest

----
## 题目地址

[https://www.lintcode.com/problem/subarray-sum-closest/description](https://www.lintcode.com/problem/subarray-sum-closest/description)

## 题目描述

```text
Given an integer array, find a subarray with sum closest to zero. Return the indexes of the first number and last number.
```

## 代码

```java
public class Solution {
    class Pair {
    int first, second;
    public Pair(int first, int second) {
      this.first = first;
      this.second = second;
    }
  }

  public Pair findSubArray(int arr[], int n) {
    int start = 0, end = 0, min_sum = Integer.MAX_VALUE;
    for (int i = 0; i < n; i++) {
      int curr_sum = arr[i];
      if (min_sum > Math.abs(curr_sum)) {
        min_sum = Math.abs(curr_sum);
        start = i;
        end = i;
      }

      for (int j = i + 1; j < n; j++) {
        curr_sum = curr_sum + arr[j];

        if (min_sum > Math.abs(curr_sum)) {
          min_sum = Math.abs(curr_sum);
          start = i;
          end = j;
        }
      }
    }

    Pair p = new Pair(start, end);
    return p;
  }
}
```

Solution 2:

```java
public class Solution {
    class Pair {
    int first, second;
    public Pair(){}
    public Pair(int first, int second) {
      this.first = first;
      this.second = second;
    }
  }

  public Pair findSubArray(int nums, int n) {
    int start, end, min_diff = Integer.MAX_VALUE;
    ArrayList<Pair> list = new ArrayList<Pair>();
    Pair p0 = new Pair(0, -1);
    for (int i = 1; i < n; i++) {
            Pair pre = list.get(i - 1);
            Pair p = new Pair();
            p.first = pre.first + nums[i - 1];
            p.second = i - 1;
            list.add(p);
        }

    list.sort(new Comparator<Pair>() {
            public int compare(Pair p1, Pair p2) {
                return p1.first - p2.first;
            }
        });

        for (int i = 1; i < n; i++) {
            int diff = list.get(i).first - list.get(i - 1).first;
            if (min_diff > diff) {
                min_diff = diff;
                start = list.get(i - 1).second;
                end = list.get(i).second;
            }
        }

        return new Pair(start, end);
  }

}
```

