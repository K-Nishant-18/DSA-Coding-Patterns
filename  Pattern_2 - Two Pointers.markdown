# Two Pointers Pattern in Java

## Overview
The Two Pointers pattern uses two pointers to traverse a data structure, often a sorted array or linked list, to solve problems efficiently.

## Use Cases
- Finding pairs or triplets with a given sum.
- Removing duplicates from a sorted array.

## Approach
1. Sort the array if needed.
2. Initialize two pointers (e.g., left and right).
3. Move pointers based on the sum or condition to find the solution.

## Example Problem: Find a Pair with Given Sum
Given a sorted array, find two numbers whose sum equals a target.

### Java Implementation
```java
public class PairSum {
    public static int[] findPair(int[] arr, int target) {
        Arrays.sort(arr);
        int left = 0, right = arr.length - 1;
        while (left < right) {
            int sum = arr[left] + arr[right];
            if (sum == target) return new int[]{arr[left], arr[right]};
            else if (sum < target) left++;
            else right--;
        }
        return new int[]{};
    }
}
```

### Explanation
- **Time Complexity**: O(n log n) due to sorting.
- **Space Complexity**: O(1).

## Navigation
[Back to README](README.md)