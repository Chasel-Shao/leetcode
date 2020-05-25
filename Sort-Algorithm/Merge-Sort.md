## 代码

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

