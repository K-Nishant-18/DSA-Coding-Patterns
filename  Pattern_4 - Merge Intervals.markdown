# Merge Intervals Pattern in Java

## Overview
The Merge Intervals pattern handles problems involving overlapping intervals by merging them into mutually exclusive intervals.

## Use Cases
- Merge overlapping intervals.
- Find non-overlapping intervals.

## Approach
1. Sort intervals by start time.
2. Iterate and merge overlapping intervals by updating end times.

## Example Problem: Merge Intervals
Given a list of intervals, merge all overlapping intervals.

### Java Implementation
```java
public class MergeIntervals {
    public static int[][] merge(int[][] intervals) {
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));
        List<int[]> result = new ArrayList<>();
        int[] current = intervals[0];
        result.add(current);
        for (int[] interval : intervals) {
            if (current[1] >= interval[0]) current[1] = Math.max(current[1], interval[1]);
            else { current =.interval; result.add(current); }
        }
        return result.toArray(new int[result.size()][]);
    }
}
```

### Explanation
- **Time Complexity**: O(n log n).
- **Space Complexity**: O(n).

## Navigation
[Back to README](README.md)