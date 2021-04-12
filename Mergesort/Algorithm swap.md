## Algorithm swap

----
## 题目地址

https://algorithms.tutorialhorizon.com/minimum-number-of-adjacent-swaps-to-sort-the-given-array/

## 题目描述
```
Minimum number of adjacent swaps to sort the given array

Given an array of integers, you are allowed to swap only adjacent elements in the array. write a program to find the minimum number of swaps to sort the given array.
```

## 代码

### Approach #1 

```java
import java.util.Arrays;                                                                                                          
                                                                                                                                  
public class AdjacentSwapToSortArray {                                                                                            
                                                                                                                                  
    public void minimumAdjacentSwapsToSortArray(int [] input){                                                                    
        System.out.println("Input[] : " + Arrays.toString(input));                                                                
        int totalInversions = divide(input, 0, input.length-1);                                                                   
        System.out.println("Minimums adjacent swaps required sort the array: " + totalInversions);                                
    }                                                                                                                             
                                                                                                                                  
    public int divide(int [] input, int low, int high){                                                                           
                                                                                                                                  
        if(low >= high)                                                                                                           
            return 0;                                                                                                             
                                                                                                                                  
        int mid = low + (high-low)/2;                                                                                             
                                                                                                                                  
        int leftSwaps = divide(input, low, mid);                                                                                  
                                                                                                                                  
        int rightSwaps = divide(input, mid+1, high);                                                                              
                                                                                                                                  
        int mergeSwaps = conquerAndCount(input, low, mid, high);                                                                  
                                                                                                                                  
        return leftSwaps + rightSwaps + mergeSwaps;                                                                               
    }                                                                                                                             
                                                                                                                                  
    public int conquerAndCount(int [] input, int leftIndex, int midIndex, int rightIndex){                                        
        // temporary left sub array                                                                                               
        int[] left = Arrays.copyOfRange(input, leftIndex, midIndex + 1);                                                          
                                                                                                                                  
        // temporary right sub array                                                                                              
        int[] right = Arrays.copyOfRange(input, midIndex + 1, rightIndex + 1);                                                    
                                                                                                                                  
        int i = 0, j = 0, k = leftIndex, inversions = 0;                                                                          
                                                                                                                                  
        while (i < left.length && j < right.length) {                                                                             
            if (left[i] <= right[j])                                                                                              
                input[k++] = left[i++];                                                                                           
            else {                                                                                                                
                input[k++] = right[j++];                                                                                          
                //count the inversions                                                                                            
                int count = (midIndex+1)-(leftIndex+i);     // left[i] > right[j]                                                                      
                inversions +=count;                                                                                               
            }                                                                                                                     
        }                                                                                                                         
                                                                                                                                  
        //fill rest of the elements from left array if any                                                                        
        while(i<left.length)                                                                                                      
            input[k++] = left[i++];                                                                                               
                                                                                                                                  
        //fill rest of the elements from right array if any                                                                       
        while(j<right.length)                                                                                                     
            input[k++] = right[j++];                                                                                              
                                                                                                                                  
        return inversions;                                                                                                        
    }                                                                                                                             
                                                                                                                                  
    public static void main(String[] args){                                                                                       
        int input[] = {10, 3, 4, 2, 5, 7, 9, 11};                                                                                 
        AdjacentSwapToSortArray s = new AdjacentSwapToSortArray();                                                                
        s.minimumAdjacentSwapsToSortArray(input);                                                                                 
    }                                                                                                                             
}    
```



Q2

```
Given an array and a sorting algorithm, the sorting algorithm will do a selection swap. Find the number of swaps to sort the array.

For example the initical array is [5, 4, 1, 2], this is how the sorting algorithm works:
Swap index 0 with 1 to form the sorted array [4, 5, 1, 2].
Swap index 0 with 2 to form the sorted array [1, 5, 4, 2].
Swap index 1 with 2 to form the sorted array [1, 4, 5, 2].
Swap index 1 with 3 to form the sorted array [1, 2, 5, 4].
Swap index 2 with 3 to form the sorted array [1, 2, 4, 5].

Constraints
1 <= n <= 10^5
1 <= arr[i] <= 10^9
all elements of arr are unique


Example:
arr = [8, 2, 3]
return 2
explanation:
Swap a[0] and a[1]. The resulting array is [2, 8, 3].
Swap a[1] and a[2]. The resulting array is [2, 3, 8].
Return the number of swaps which is 2.
```













