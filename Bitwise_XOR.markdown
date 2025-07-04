# Bitwise XOR Pattern in Java

## Overview
The Bitwise XOR pattern uses XOR properties to solve problems involving finding unique or missing numbers.

## Use Cases
- Find a single number in an array where others appear twice.
- Find missing numbers in a range.

## Approach
1. Use XOR’s properties: a ⊕ a = 0, a ⊕ 0 = a.
2. XOR all elements to find the unique or missing number.

## Example Problem: Single Number
Given an array where every number appears twice except one, find that number.

### Java Implementation
```java
public class SingleNumber {
    public static int singleNumber(int[] nums) {
        int result = 0;
        for (int num : nums) {
            result ^= num;
        }
        return result;
    }
}
```

### Explanation
- **Time Complexity**: O(n).
- **Space Complexity**: O(1).

## Navigation
[Back to README](README.md)