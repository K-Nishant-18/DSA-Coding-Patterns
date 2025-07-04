# Cyclic Sort Pattern in Java

## Overview
The Cyclic Sort pattern sorts arrays with numbers in a specific range by placing each number at its correct index.

## Use Cases
- Find missing numbers in range 1 to n.
- Find duplicates in an array.

## Approach
1. Iterate through the array.
2. Swap elements to place each number at its correct index (value - 1).

## Example Problem: Find Missing Number
Find the missing number in an array of range 0 to n.

### Java Implementation
```java
public class MissingNumber {
    public static int findMissingNumber(int[] arr) {
        int i = 0;
        while (i < arr.length) {
            int correct = arr[i];
            if (arr[i] < arr.length && arr[i] != arr[correct]) {
                int temp = arr[i];
                arr[i] = arr[correct];
                arr[correct] = temp;
            } else i++;
        }
        for (i = 0; i < arr.length; i++) {
            if (arr[i] != i) return i;
        }
        return arr.length;
    }
}
```

### Explanation
- **Time Complexity**: O(n).
- **Space Complexity**: O(1).

## Navigation
[Back to README](README.md)