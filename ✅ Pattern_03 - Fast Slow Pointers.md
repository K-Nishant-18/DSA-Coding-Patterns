# Fast & Slow Pointers Pattern in Java

## Overview
The Fast & Slow Pointers pattern uses two pointers moving at different speeds to detect cycles or find midpoints in linked lists.

## Use Cases
- Detect cycles in a linked list.
- Find the middle of a linked list.

## Approach
1. Initialize two pointers: slow (moves one step) and fast (moves two steps).
2. Traverse until they meet (indicating a cycle) or fast reaches the end.

## Example Problem: Detect Cycle in Linked List
Given a linked list, determine if it has a cycle.

### Java Implementation
```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int val) { this.val = val; }
}

public class CycleDetection {
    public static boolean hasCycle(ListNode head) {
        ListNode slow = head, fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) return true;
        }
        return false;
    }
}
```

### Explanation
- **Time Complexity**: O(n).
- **Space Complexity**: O(1).

## Navigation
[Back to README](README.md)