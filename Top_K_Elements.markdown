# Top K Elements Pattern in Java

## Overview
The Top K Elements pattern uses a heap or quickselect to find the top, smallest, or most frequent K elements in a dataset.

## Use Cases
- Find the K largest numbers.
- Find the K most frequent elements.

## Approach
1. Use a min heap to keep track of the top K elements.
2. Alternatively, use quickselect for average O(n) time.

## Example Problem: Top K Frequent Elements
Given an array, find the K most frequent elements.

### Java Implementation
```java
import java.util.*;

public class TopKFrequent {
    public static int[] topKFrequent(int[] nums, int k) {
        Map<Integer, Integer> freq = new HashMap<>();
        for (int num : nums) freq.put(num, freq.getOrDefault(num, 0) + 1);
        PriorityQueue<Integer> minHeap = new PriorityQueue<>((a, b) -> freq.get(a) - freq.get(b));
        for (int num : freq.keySet()) {
            minHeap.offer(num);
            if (minHeap.size() > k) minHeap.poll();
        }
        int[] result = new int[k];
        for (int i = k - 1; i >= 0; i--) result[i] = minHeap.poll();
        return result;
    }
}
```

### Explanation
- **Time Complexity**: O(n log k).
- **Space Complexity**: O(n).

## Navigation
[Back to README](README.md)