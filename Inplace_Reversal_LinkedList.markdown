# In-place Reversal of a LinkedList Pattern in Java

## Overview
This pattern reverses a linked list or its sublists in-place by manipulating pointers.

## Use Cases
- Reverse a linked list.
- Reverse every K nodes.

## Approach
1. Use three pointers (prev, current, next) to reverse links.
2. Iterate and update pointers to reverse the list.

## Example Problem: Reverse Linked List
Reverse a singly linked list.

### Java Implementation
```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int val) { this.val = val; }
}

public class ReverseLinkedList {
    public static ListNode reverse(ListNode head) {
        ListNode prev = null, current = head;
        while (current != null) {
            ListNode next = current.next;
            current.next = prev;
            prev = current;
            current = next;
        }
        return prev;
    }
}
```

### Explanation
- **Time Complexity**: O(n).
- **Space Complexity**: O(1).

## Navigation
[Back to README](README.md)