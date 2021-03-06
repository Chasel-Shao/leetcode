## 代码

### Approach #1 Iterative - Select the middle index as Pivot

```java
class Solution {
  public void quickSort(int[] arr, int low, int high) {
    if (arr == null || arr.length == 0) return;
    if (low >= high) return;

    int middle = low + (high - low) / 2;
    int pivot = arr[middle];

    int i = low, j = high;
    while (i <= j) {
      while (arr[i] < pivot) {
        i++;
      }
      while (arr[j] > pivot) {
        j--;
      }

      if (i <= j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
        i++;
        j--;
      }
    }

    if (low < j) {
      quickSort(arr, low, j);
    }    
    if (high > i) {
      quickSort(arr, i, high);
    }

  }
}
```

### Approach #2 Select the last value of the array as Pivot

```java
class Solution {
  public void quickSort(int[] arr, int start, int end) {
    int partition = partition(arr, start, end);

    if (start < partition - 1) {
        quickSort(arr, start, partition - 1);
    }

    if (partition + 1 < end) {
        quickSort(arr, partition + 1, end);
    }
  }

  public int partition(int[] arr, int start, int end) {
    int pivot = arr[end];
    for (int i = start; i < end; i++) {
      if (arr[i] < pivot) {
        swap(arr, start, i);
        start++;
      }
    }

		swap(arr, start, end);
    
    return start;
  }
  
  private void swap(int[] arr, i, j) {
    int temp = arr[i];
    arr[i] = arr[j];
    arr[j] = temp;
  }
}
```

