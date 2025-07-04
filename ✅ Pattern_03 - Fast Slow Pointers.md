# 🐰🐢 Fast & Slow Pointers Pattern

## 📖 What is Fast & Slow Pointers?

Imagine a race between a rabbit and a turtle on a circular track. The rabbit runs twice as fast as the turtle. If there's a loop in the track, they'll eventually meet! If there's no loop, the rabbit will reach the end first. That's exactly what the **Fast & Slow Pointers** pattern does in programming!

The Fast & Slow Pointers pattern uses two pointers that move at different speeds through a data structure (usually a linked list) to detect cycles, find midpoints, or solve other problems efficiently.

```
┌─────────────────────────────────────────────────────────┐
│  Fast & Slow Pointers in Action                       │
│                                                       │
│  Linked List: 1 → 2 → 3 → 4 → 5 → 6 → 3 (cycle)     │
│                                                       │
│  Initial: slow → fast →                               │
│  1 → 2 → 3 → 4 → 5 → 6 → 3                          │
│                                                       │
│  Step 1: slow → fast →                                │
│  1 → 2 → 3 → 4 → 5 → 6 → 3                          │
│                                                       │
│  Step 2: slow → fast →                                │
│  1 → 2 → 3 → 4 → 5 → 6 → 3                          │
│                                                       │
│  Eventually they meet at node 3!                      │
└─────────────────────────────────────────────────────────┘
```

## 🎯 When to Use Fast & Slow Pointers?

### ✅ Perfect for:
- **Cycle detection**: "Detect if linked list has a cycle"
- **Finding middle**: "Find middle node of linked list"
- **Palindrome detection**: "Check if linked list is palindrome"
- **Duplicate detection**: "Find duplicate number in array"
- **Happy number**: "Check if number is happy"
- **Linked list problems**: "Find intersection of two lists"

### ❌ Not suitable for:
- Problems requiring random access to elements
- When you need to maintain order of elements
- Problems that can be solved with simple iteration

## 🧠 How Does It Work?

### The Algorithm Steps:

1. **Initialize**: Set slow = head, fast = head
2. **Move pointers**: slow moves 1 step, fast moves 2 steps
3. **Check conditions**: 
   - If fast reaches end → no cycle
   - If slow == fast → cycle detected
4. **Continue**: Until condition is met

### Visual Representation:

```
┌─────────────────────────────────────────────────────────┐
│  Step-by-Step Movement                                │
│                                                       │
│  Initial: slow → fast →                               │
│  1 → 2 → 3 → 4 → 5 → 6 → 3                          │
│                                                       │
│  Step 1: slow → fast →                                │
│  1 → 2 → 3 → 4 → 5 → 6 → 3                          │
│                                                       │
│  Step 2: slow → fast →                                │
│  1 → 2 → 3 → 4 → 5 → 6 → 3                          │
│                                                       │
│  Step 3: slow → fast →                                │
│  1 → 2 → 3 → 4 → 5 → 6 → 3                          │
│                                                       │
│  They meet! Cycle detected!                           │
└─────────────────────────────────────────────────────────┘
```

## 💡 Example 1: Detect Cycle in Linked List

### Problem Statement
Given a linked list, determine if it has a cycle in it.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  Linked List with Cycle                               │
│                                                       │
│  1 → 2 → 3 → 4 → 5 → 6 → 3 (back to 3)              │
│                                                       │
│  Initial: slow → fast →                               │
│  1 → 2 → 3 → 4 → 5 → 6 → 3                          │
│                                                       │
│  Step 1: slow → fast →                                │
│  1 → 2 → 3 → 4 → 5 → 6 → 3                          │
│                                                       │
│  Step 2: slow → fast →                                │
│  1 → 2 → 3 → 4 → 5 → 6 → 3                          │
│                                                       │
│  Step 3: slow → fast →                                │
│  1 → 2 → 3 → 4 → 5 → 6 → 3                          │
│                                                       │
│  They meet at node 3! Cycle detected!                │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int val) { 
        this.val = val; 
    }
}

public class CycleDetection {
    public static boolean hasCycle(ListNode head) {
        // Edge cases
        if (head == null || head.next == null) {
            return false;
        }

        ListNode slow = head;
        ListNode fast = head;

        // Move slow by 1, fast by 2
        while (fast != null && fast.next != null) {
            slow = slow.next;           // Move 1 step
            fast = fast.next.next;      // Move 2 steps
            
            if (slow == fast) {
                return true; // Cycle detected!
            }
        }

        return false; // No cycle
    }

    public static void main(String[] args) {
        // Create a linked list with cycle: 1 → 2 → 3 → 4 → 5 → 6 → 3
        ListNode head = new ListNode(1);
        ListNode node2 = new ListNode(2);
        ListNode node3 = new ListNode(3);
        ListNode node4 = new ListNode(4);
        ListNode node5 = new ListNode(5);
        ListNode node6 = new ListNode(6);

        head.next = node2;
        node2.next = node3;
        node3.next = node4;
        node4.next = node5;
        node5.next = node6;
        node6.next = node3; // Creates cycle back to node3

        System.out.println("Linked list: 1 → 2 → 3 → 4 → 5 → 6 → 3 (cycle)");
        System.out.println("Has cycle: " + hasCycle(head));
        
        // Output:
        // Linked list: 1 → 2 → 3 → 4 → 5 → 6 → 3 (cycle)
        // Has cycle: true
    }
}
```

### Time & Space Complexity
- **Time Complexity**: O(n) - We traverse the list at most once
- **Space Complexity**: O(1) - We use only two pointers

## 💡 Example 2: Find Middle of Linked List

### Problem Statement
Given a linked list, find the middle node. If there are two middle nodes, return the second one.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  Linked List: 1 → 2 → 3 → 4 → 5 → 6                  │
│                                                       │
│  Initial: slow → fast →                               │
│  1 → 2 → 3 → 4 → 5 → 6                               │
│                                                       │
│  Step 1: slow → fast →                                │
│  1 → 2 → 3 → 4 → 5 → 6                               │
│                                                       │
│  Step 2: slow → fast →                                │
│  1 → 2 → 3 → 4 → 5 → 6                               │
│                                                       │
│  Step 3: slow → fast →                                │
│  1 → 2 → 3 → 4 → 5 → 6                               │
│                                                       │
│  Fast reaches end, slow is at middle (4)              │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
public class FindMiddle {
    public static ListNode findMiddle(ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }

        ListNode slow = head;
        ListNode fast = head;

        // Move fast twice as fast as slow
        while (fast != null && fast.next != null) {
            slow = slow.next;           // Move 1 step
            fast = fast.next.next;      // Move 2 steps
        }

        return slow; // slow is at middle
    }

    public static void main(String[] args) {
        // Create linked list: 1 → 2 → 3 → 4 → 5 → 6
        ListNode head = new ListNode(1);
        head.next = new ListNode(2);
        head.next.next = new ListNode(3);
        head.next.next.next = new ListNode(4);
        head.next.next.next.next = new ListNode(5);
        head.next.next.next.next.next = new ListNode(6);

        System.out.println("Linked list: 1 → 2 → 3 → 4 → 5 → 6");
        
        ListNode middle = findMiddle(head);
        System.out.println("Middle node: " + middle.val);
        
        // Output:
        // Linked list: 1 → 2 → 3 → 4 → 5 → 6
        // Middle node: 4
    }
}
```

## 💡 Example 3: Find Duplicate Number

### Problem Statement
Given an array containing n+1 integers where each integer is between 1 and n, find the duplicate number.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  Array: [1, 3, 4, 2, 2] (n=4, array size=5)         │
│                                                       │
│  Treat as linked list:                                │
│  1 → 3 → 2 → 4 → 2 (cycle at 2)                      │
│                                                       │
│  Initial: slow → fast →                               │
│  1 → 3 → 2 → 4 → 2                                   │
│                                                       │
│  Step 1: slow → fast →                                │
│  1 → 3 → 2 → 4 → 2                                   │
│                                                       │
│  Step 2: slow → fast →                                │
│  1 → 3 → 2 → 4 → 2                                   │
│                                                       │
│  They meet! Duplicate is 2                            │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
public class FindDuplicate {
    public static int findDuplicate(int[] nums) {
        if (nums == null || nums.length < 2) {
            return -1;
        }

        // Phase 1: Find intersection point
        int slow = nums[0];
        int fast = nums[0];

        do {
            slow = nums[slow];
            fast = nums[nums[fast]];
        } while (slow != fast);

        // Phase 2: Find entrance to cycle
        slow = nums[0];
        while (slow != fast) {
            slow = nums[slow];
            fast = nums[fast];
        }

        return slow; // This is the duplicate
    }

    public static void main(String[] args) {
        int[] nums = {1, 3, 4, 2, 2};
        
        System.out.println("Array: " + java.util.Arrays.toString(nums));
        System.out.println("Duplicate number: " + findDuplicate(nums));
        
        // Output:
        // Array: [1, 3, 4, 2, 2]
        // Duplicate number: 2
    }
}
```

## 🎯 Common Patterns & Templates

### Template 1: Basic Cycle Detection
```java
public boolean hasCycle(ListNode head) {
    if (head == null || head.next == null) {
        return false;
    }

    ListNode slow = head;
    ListNode fast = head;

    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
        
        if (slow == fast) {
            return true;
        }
    }

    return false;
}
```

### Template 2: Find Middle Node
```java
public ListNode findMiddle(ListNode head) {
    if (head == null || head.next == null) {
        return head;
    }

    ListNode slow = head;
    ListNode fast = head;

    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
    }

    return slow;
}
```

### Template 3: Find Cycle Start
```java
public ListNode detectCycle(ListNode head) {
    if (head == null || head.next == null) {
        return null;
    }

    // Phase 1: Find intersection
    ListNode slow = head;
    ListNode fast = head;

    do {
        slow = slow.next;
        fast = fast.next.next;
    } while (slow != fast && fast != null && fast.next != null);

    if (slow != fast) {
        return null; // No cycle
    }

    // Phase 2: Find cycle start
    slow = head;
    while (slow != fast) {
        slow = slow.next;
        fast = fast.next;
    }

    return slow;
}
```

## 🚀 Practice Problems

### 🟢 Easy Level (5 Problems)
1. **[Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)** - Basic cycle detection
2. **[Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)** - Find middle node
3. **[Happy Number](https://leetcode.com/problems/happy-number/)** - Cycle detection with number theory
4. **[Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)** - Array as linked list
5. **[Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)** - Find middle and reverse

### 🟡 Medium Level (3 Problems)
1. **[Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)** - Find cycle start point
2. **[Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)** - Fast/slow with offset
3. **[Reorder List](https://leetcode.com/problems/reorder-list/)** - Find middle and merge

### 🔴 Hard Level (2 Problems)
1. **[Sort List](https://leetcode.com/problems/sort-list/)** - Merge sort with fast/slow
2. **[Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/)** - Complex cycle detection

## 🎨 Key Takeaways

### ✅ Do's:
- Always check for null pointers before accessing next
- Use different speeds (usually 1:2 ratio)
- Handle edge cases (empty list, single node)
- Consider both phases for cycle detection (find intersection, then find start)

### ❌ Don'ts:
- Don't forget to check fast.next != null before fast.next.next
- Don't assume the list has a cycle without checking
- Don't use this pattern when simple iteration is sufficient
- Don't ignore the case where fast reaches the end

### 🧠 Memory Aids:
- **"Rabbit and turtle race"**
- **"Fast moves twice as fast as slow"**
- **"If they meet, there's a cycle"**

## 🔍 Debugging Tips

1. **Print pointer values** at each step to visualize movement
2. **Check for null pointers** before accessing next
3. **Verify the meeting point** - where do they actually meet?
4. **Test with edge cases** - empty list, single node, two nodes

## 📚 Further Reading

- [GeeksforGeeks - Floyd's Cycle Finding Algorithm](https://www.geeksforgeeks.org/floyds-cycle-finding-algorithm/)
- [LeetCode - Fast and Slow Pointers Problems](https://leetcode.com/tag/fast-and-slow-pointers/)

---

**🎉 Congratulations!** You've mastered the Fast & Slow Pointers pattern. Practice with the problems above to solidify your understanding!

---

**[← Back to README](README.md)** | **[Next Pattern →](Merge_Intervals.markdown)**