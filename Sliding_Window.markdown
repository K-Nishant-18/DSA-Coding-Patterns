# Sliding Window Pattern in Java

## Overview
The **Sliding Window** pattern is used to solve problems involving contiguous subarrays or substrings, such as finding the maximum sum of a subarray of size K or the longest substring with certain constraints. The pattern maintains a "window" that slides over the data structure, expanding or shrinking dynamically to optimize computation.

## Use Cases
- Finding the maximum/minimum sum of a subarray of fixed size.
- Identifying the longest substring with at most K distinct characters.
- Solving problems like maximum average subarray or string anagrams.

## Approach
1. Initialize a window with two pointers (start and end) or track window boundaries.
2. Slide the window by moving the end pointer to expand it and the start pointer to shrink it when needed.
3. Maintain relevant information (e.g., sum, count, or frequency map) within the window.
4. Update the result based on the problem’s requirements (e.g., maximum sum, longest length).
5. Optimize by avoiding redundant calculations.

## Example Problem: Maximum Sum Subarray of Size K
Given an array of integers and a number K, find the maximum sum of any contiguous subarray of size K.

### Java Implementation
```java
public class MaxSumSubarray {
    public static int findMaxSumSubarray(int[] arr, int k) {
        if (arr == null || k <= 0 || k > arr.length) {
            throw new IllegalArgumentException("Invalid input");
        }

        // Calculate sum of first window of size k
        int windowSum = 0;
        for (int i = 0; i < k; i++) {
            windowSum += arr[i];
        }

        // Initialize maxSum with the first window's sum
        int maxSum = windowSum;

        // Slide the window and update maxSum
        for (int i = k; i < arr.length; i++) {
            windowSum = windowSum + arr[i] - arr[i - k]; // Add next element, remove first element of previous window
            maxSum = Math.max(maxSum, windowSum);
        }

        return maxSum;
    }

    public static void main(String[] args) {
        int[] arr = {1, 4, 2, 10, 2, 3, 1, 0, 20};
        int k = 4;
        System.out.println("Maximum sum of subarray of size " + k + ": " + findMaxSumSubarray(arr, k));
        // Output: Maximum sum of subarray of size 4: 24
        // Explanation: Subarray [4, 2, 10, 2] has the maximum sum of 24.
    }
}
```

### Explanation
- **Input**: Array `[1, 4, 2, 10, 2, 3, 1, 0, 20]` and `k = 4`.
- **Step 1**: Compute the sum of the first window (`[1, 4, 2, 10]` = 17).
- **Step 2**: Slide the window by adding the next element and subtracting the first element of the previous window (e.g., for `[4, 2, 10, 2]`, sum = 17 + 2 - 1 = 18).
- **Step 3**: Track the maximum sum encountered (`24` for `[4, 2, 10, 2]`).
- **Time Complexity**: O(n), where n is the array length (single pass after initial window).
- **Space Complexity**: O(1), as we only use a few variables.

## Practice Problems
- LeetCode: [Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/)
- LeetCode: [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

## Navigation
[Back to README](README.md)