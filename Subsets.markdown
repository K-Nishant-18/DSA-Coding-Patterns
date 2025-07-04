# Subsets Pattern in Java

## Overview
The Subsets pattern generates all possible subsets or permutations of a set using backtracking or iterative methods.

## Use Cases
- Generate all subsets of a set.
- Find all unique permutations.

## Approach
1. Use backtracking to include or exclude each element.
2. Build subsets incrementally, storing valid combinations.

## Example Problem: Generate All Subsets
Given a set of distinct integers, return all possible subsets.

### Java Implementation
```java
import java.util.ArrayList;
import java.util.List;

public class Subsets {
    public static List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        backtrack(nums, 0, new ArrayList<>(), result);
        return result;
    }

    private static void backtrack(int[] nums, int start, List<Integer> current, List<List<Integer>> result) {
        result.add(new ArrayList<>(current));
        for (int i = start; i < nums.length; i++) {
            current.add(nums[i]);
            backtrack(nums, i + 1, current, result);
            current.remove(current.size() - 1);
        }
    }
}
```

### Explanation
- **Time Complexity**: O(2^n), as each element can be included or excluded.
- **Space Complexity**: O(n * 2^n) for storing all subsets.

## Navigation
[Back to README](README.md)