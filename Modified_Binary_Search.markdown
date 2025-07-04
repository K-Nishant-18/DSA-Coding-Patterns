# Modified Binary Search Pattern in Java

## Overview
The Modified Binary Search pattern adapts binary search for problems involving sorted arrays with variations, such as finding boundaries or the closest element.

## Use Cases
- Find the first or last occurrence of an element.
- Search for the element with the minimum difference from a key.

## Approach
1. Apply binary search with modified conditions.
2. Adjust the mid-point logic to handle specific cases (e.g., first occurrence).

## Example Problem: Find First and Last Position
Given a sorted array, find the starting and ending position of a target value.

### Java Implementation
```java
public class FirstLastPosition {
    public static int[] searchRange(int[] nums, int target) {
        int[] result = {-1, -1};
        result[0] = findBound(nums, target, true);
        result[1] = findBound(nums, target, false);
        return result;
    }

    private static int findBound(int[] nums, int target, boolean first) {
        int left = 0, right = nums.length - 1, bound = -1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] == target) {
                bound = mid;
                if (first) right = mid - 1;
                else left = mid + 1;
            } else if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return bound;
    }
}
```

### Explanation
- **Time Complexity**: O(log n) for each bound.
- **Space Complexity**: O(1).

## Navigation
[Back to README](README.md)