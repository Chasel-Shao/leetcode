## 代码

### Approach  #1

```java
class Solution {
  public void bubbleSort(int[] a, int n) {
    for (int i = 0; i < n - 1; ++i) {
      // Tranversing from left to right
      for (int j = 0; j < n-i-1; ++j) {
        // Ascending order
        if (a[j] > a[j + 1]) {
            int temp;
            temp = a[j + 1];
            a[j + 1] = a[j];
            a[j] = temp;
        }

      }
    }
  }
}
```

