# K-way Merge Pattern in Java

## Overview
The K-way Merge pattern merges K sorted arrays or lists using a min heap to maintain sorted order.

## Use Cases
- Merge K sorted lists.
- Find the smallest range covering elements from K lists.

## Approach
1. Use a min heap to store the smallest element from each list.
2. Pop the smallest element and add the next element from the same list.

## Example Problem: Merge K Sorted Lists
Merge K sorted linked lists into one sorted linked list.

### Java Implementation
```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int val) { this.val = val; }
}

public class MergeKSortedLists {
    public static ListNode mergeKLists(ListNode[] lists) {
        PriorityQueue<ListNode> minHeap = new PriorityQueue<>((a, b) -> a.val - b.val);
        for (ListNode node : lists) if (node != null) minHeap.offer(node);
        ListNode dummy = new ListNode(0), current = dummy;
        while (!minHeap.isEmpty()) {
            ListNode node = minHeap.poll();
            current.next = node;
            current = current.next;
            if (node.next != null) minHeap.offer(node.next);
        }
        return dummy.next;
    }
}
```

### Explanation
- **Time Complexity**: O(n log k), where n is total nodes, k is number of lists.
- **Space Complexity**: O(k).

## Navigation
[Back to README](README.md)