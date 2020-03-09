# 代码

Version 0:

```java
class BubbleSort 
{ 
    void bubbleSort(int arr[]) 
    { 
        int n = arr.length; 
        for (int i = 0; i < n-1; i++) 
            for (int j = 0; j < n-i-1; j++) 
                if (arr[j] > arr[j+1]) 
                { 
                    // swap arr[j+1] and arr[i] 
                    int temp = arr[j]; 
                    arr[j] = arr[j+1]; 
                    arr[j+1] = temp; 
                } 
    } 
}
```

Version 1:

```java
class Solution {
    public void bubbleSort(int[] a, int n) {
        for (int i = 0; i < n; ++i) {
            // Tranversing from left to right
            for (int j = 0; j + 1 < n; ++j) {
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

Version 2:

```java
class Solution {
    public void bubbleSort(int[] a, int n) {
        for (int i = 0; i < n; ++i) {
            // Tranversing from right to left
            for (int j =  n - 1; j - i - 1 >= 0; --j) {
                // Ascending order
                if (a[j - 1] > a[j]) {
                    int temp;
                    temp = a[j - 1];
                    a[j - 1] = a[j];
                    a[j] = temp;
                }

            }
        }
    }
}
```

