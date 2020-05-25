## Interleaving Positive And Negative Numbers

----
## 题目地址

[https://www.lintcode.com/problem/interleaving-positive-and-negative-numbers](https://www.lintcode.com/problem/interleaving-positive-and-negative-numbers)

## 题目描述

```text
Given an array with positive and negative integers. Re-range it to interleaving with positive and negative integers.
```

## 代码

```java
public class Solution {
    public void rearrange(int arr[], int n) {
    int i = -1, temp = 0;
      // 1. 先把负数放前
    for (int j = 0; j < n; j++) {
      if (arr[j] < 0) {
        i++;
        temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
      }
    }

    int pos = i + 1, neg = 0;
		// 2. 把正数往前面负数群中交换
    while (pos < n && neg < pos && arr[neg] < 0) {
      temp = arr[neg];
      arr[neg] = arr[pos];
      arr[pos] = temp;
      pos++;
      neg += 2;
    }
  }

}
```

