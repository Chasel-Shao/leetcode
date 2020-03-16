## Sort Colors Ii

----
## 题目地址

[https://www.lintcode.com/problem/sort-colors-ii](https://www.lintcode.com/problem/sort-colors-ii)

## 题目描述

```text
Given an array of n objects with k different colors (numbered from 1 to k), sort them so that objects of the same color are adjacent, with the colors in the order 1, 2, ... k.
```

## 代码

```java
public class Solution {
    public void sortColors2(int[] colors, int k) {
    if (colors == null || colors.length == 0) return;

    rainbowSort(colors, 0, colors.length - 1, 1, k);
  }

  public void rainbowSort(int[] colrs,
                         int left,
                         int right,
                         int colorFrom,
                         int colorTo) {
    if (colorFrom == colorTo) return;
    if (left >= right) return;

    int colorMid = (colorFrom + colorTo) / 2;
    int l = left, r = right;
    while (l <= r) {
      while (l <= r && colors[l] <= colorMid) {
        l++;
      }
      while (l <= r && colors[r] > colorMid) {
        r--;
      }
      if (l <= r) {
        int temp = colors[l];
        colors[l] = colors[r];
        colors[r] = temp;
        l++;
        r--;
      }
    }

    rainbowSort(colors, left, r, colorFrom, colorMid);
    rainbowSort(colors, l, right, colorMid + 1, colorTo);
  }
}
```

