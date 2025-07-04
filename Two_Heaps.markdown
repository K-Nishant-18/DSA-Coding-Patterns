# Two Heaps Pattern in Java

## Overview
The Two Heaps pattern uses two priority queues (a max heap and a min heap) to maintain balanced data, often for finding medians or scheduling tasks in a stream of data.

## Use Cases
- Find the median of a number stream.
- Schedule tasks with deadlines.

## Approach
1. Use a max heap for the lower half of numbers and a min heap for the upper half.
2. Keep heaps balanced (difference in sizes ≤ 1).
3. The median is the average of the top elements of both heaps or the top of the larger heap.

## Example Problem: Find Median from Data Stream
Given a stream of integers, find the median at any point.

### Java Implementation
```java
import java.util.PriorityQueue;

public class MedianFinder {
    PriorityQueue<Integer> maxHeap; // Lower half
    PriorityQueue<Integer> minHeap; // Upper half

    public MedianFinder() {
        maxHeap = new PriorityQueue<>((a, b) -> b - a);
        minHeap = new PriorityQueue<>();
    }

    public void addNum(int num) {
        if (maxHeap.isEmpty() || num <= maxHeap.peek()) {
            maxHeap.offer(num);
        } else {
            minHeap.offer(num);
        }
        // Balance heaps
        if (maxHeap.size() > minHeap.size() + 1) {
            minHeap.offer(maxHeap.poll());
        } else if (minHeap.size() > maxHeap.size()) {
            maxHeap.offer(minHeap.poll());
        }
    }

    public double findMedian() {
        if (maxHeap.size() == minHeap.size()) {
            return (maxHeap.peek() + minHeap.peek()) / 2.0;
        }
        return maxHeap.peek();
    }
}
```

### Explanation
- **Time Complexity**: O(log n) for adding a number, O(1) for finding the median.
- **Space Complexity**: O(n) for storing numbers in heaps.

## Navigation
[Back to README](README.md)