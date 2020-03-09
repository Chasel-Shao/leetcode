# 代码

Version 1:

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

Version 2:

```java
class Solution {
    public void quickSort(int[] arr, int low, int high) {
        int partition = partition(arr, start, end);

        if (partition - 1 > start) {
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
                int temp = arr[start];
                arr[start] = arr[i];
                arr[i] = temp;
                start++;
            }
        }

        int temp = arr[start];
        arr[start] = pivot;
        arr[end] = temp;

        return start;
    }
}
```

