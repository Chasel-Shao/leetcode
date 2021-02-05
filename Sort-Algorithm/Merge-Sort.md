## 代码

### Approach #1

```java
public void mergeSort(int[] a, int low, int high) {
  int mid = (low + high) / 2;
  if (low < high) {
    // 左边
    mergeSort(a, low, mid);
    // 右边
    mergeSort(a, mid + 1, high);
    // 左右归并
    merge(a, low, mid, high);
    System.out.println(Arrays.toString(a));
  }
}

public void merge(int[] a, int low, int mid, int high) {
  int[] temp = new int[high - low + 1];
  int i = low;	// 左指针
  int j = mid + 1;	// 右指针
  int k = 0;
  // 把较小的数先移到新数组中
  while (i <= mid && j <= high) {
    if (a[i] < a[j]) {
        temp[k++] = a[i++];
    } else {
        temp[k++] = a[j++];
    }
  }
  // 把左边剩余的数移入数组
  while (i <= mid) {
      temp[k++] = a[i++];
  }
  // 把右边边剩余的数移入数组
  while (j <= high) {
      temp[k++] = a[j++];
  }
  // 把新数组中的数覆盖nums数组
  for (int k2 = 0; k2 < temp.length; k2++) {
      a[k2 + low] = temp[k2];
  }
}
```

### Approach #2

```java
class Solution {
  public ArrayList<Integer> mergeSort(ArrayList<Integer> array){
    int size = array.size();
    if (size < 2) {
      return array;
    }

    int middle = size / 2;
    List<Integer> left = array.subList(0, middle);
    List<Integer> right = array.subList(middle, size);

    ArrayList<Integer> leftArray = new ArrayList<Integer>();
    leftArray.addAll(left);
    ArrayList<Integer> rightArray = new ArrayList<Integer>();
    rightArray.addAll(right);

    return merge(mergeSort(leftArray), mergeSort(rightArray));
  }

  public ArrayList<Integer> merge(ArrayList<Integer> left, ArrayList<Integer> right) {
    ArrayList<Integer> result = new ArrayList<Integer>();
    while (left.size() > 0 && right.size() > 0) {
      if (left.get(0) <= right.get(0)) {
          result.add(left.get(0));
          left.remove(0);
      } else {
          result.add(right.get(0));
          right.remove(0);
      }
    }

    if (left.size() > 0) {
        result.addAll(left);
    }
    if (right.size() > 0) {
        result.addAll(right);
    }

    return result;
  }
}
```

