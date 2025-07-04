# 👆👆 Two Pointers Pattern

## 📖 What is Two Pointers?

Imagine you're reading a book with two bookmarks - one at the beginning and one at the end. You can move either bookmark forward or backward to find what you're looking for. That's exactly what the **Two Pointers** pattern does in programming!

The Two Pointers pattern uses two pointers (indices) that move through a data structure (usually an array or linked list) to solve problems efficiently. The pointers can move in the same direction, opposite directions, or at different speeds.

```
┌─────────────────────────────────────────────────────────┐
│  Two Pointers Moving in Opposite Directions           │
│                                                       │
│  Array: [1, 2, 3, 4, 5, 6, 7, 8, 9]                │
│                                                       │
│  left → ← right                                       │
│   ↓         ↓                                         │
│  [1, 2, 3, 4, 5, 6, 7, 8, 9]                        │
│                                                       │
│  After some moves:                                    │
│     left → ← right                                    │
│      ↓         ↓                                      │
│  [1, 2, 3, 4, 5, 6, 7, 8, 9]                        │
└─────────────────────────────────────────────────────────┘
```

## 🎯 When to Use Two Pointers?

### ✅ Perfect for:
- **Sorted array problems**: "Find pair with given sum"
- **Palindrome problems**: "Check if string is palindrome"
- **Remove duplicates**: "Remove duplicates from sorted array"
- **Linked list problems**: "Find middle of linked list"
- **Array partitioning**: "Move zeros to end"
- **Container problems**: "Container with most water"

### ❌ Not suitable for:
- Unsorted arrays (unless you sort first)
- Problems requiring all possible combinations
- When you need to maintain order of elements

## 🧠 Types of Two Pointers

### 1. Opposite Direction Pointers
Pointers start from opposite ends and move toward each other.

```
┌─────────────────────────────────────────────────────────┐
│  Opposite Direction Movement                           │
│                                                       │
│  Initial: left → ← right                              │
│  [1, 2, 3, 4, 5, 6, 7, 8, 9]                        │
│                                                       │
│  Step 1: left → ← right                              │
│  [1, 2, 3, 4, 5, 6, 7, 8, 9]                        │
│                                                       │
│  Step 2: left → ← right                              │
│  [1, 2, 3, 4, 5, 6, 7, 8, 9]                        │
│                                                       │
│  Continue until they meet...                          │
└─────────────────────────────────────────────────────────┘
```

### 2. Same Direction Pointers
Both pointers start from the same end and move in the same direction.

```
┌─────────────────────────────────────────────────────────┐
│  Same Direction Movement                               │
│                                                       │
│  Initial: slow → fast →                               │
│  [1, 2, 3, 4, 5, 6, 7, 8, 9]                        │
│                                                       │
│  Step 1: slow → fast →                                │
│  [1, 2, 3, 4, 5, 6, 7, 8, 9]                        │
│                                                       │
│  Step 2: slow → fast →                                │
│  [1, 2, 3, 4, 5, 6, 7, 8, 9]                        │
│                                                       │
│  Fast moves faster than slow...                       │
└─────────────────────────────────────────────────────────┘
```

### 3. Fast and Slow Pointers
One pointer moves faster than the other (usually 2x speed).

```
┌─────────────────────────────────────────────────────────┐
│  Fast and Slow Pointers                               │
│                                                       │
│  Initial: slow → fast →                               │
│  [1, 2, 3, 4, 5, 6, 7, 8, 9]                        │
│                                                       │
│  Step 1: slow → fast →                                │
│  [1, 2, 3, 4, 5, 6, 7, 8, 9]                        │
│                                                       │
│  Step 2: slow → fast →                                │
│  [1, 2, 3, 4, 5, 6, 7, 8, 9]                        │
│                                                       │
│  Fast moves 2 steps, slow moves 1 step...            │
└─────────────────────────────────────────────────────────┘
```

## 💡 Example 1: Find Pair with Given Sum (Opposite Directions)

### Problem Statement
Given a sorted array of integers, find two numbers whose sum equals a target value.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  Array: [1, 2, 3, 4, 5, 6, 7, 8, 9]                │
│  Target: 10                                           │
│                                                       │
│  Step 1: left → ← right                              │
│  [1, 2, 3, 4, 5, 6, 7, 8, 9]                        │
│  1 + 9 = 10 ✓ Found!                                 │
│                                                       │
│  If target was 15:                                    │
│  Step 1: left → ← right                              │
│  [1, 2, 3, 4, 5, 6, 7, 8, 9]                        │
│  1 + 9 = 10 < 15, move left →                        │
│                                                       │
│  Step 2: left → ← right                              │
│  [1, 2, 3, 4, 5, 6, 7, 8, 9]                        │
│  2 + 9 = 11 < 15, move left →                        │
│                                                       │
│  Continue until sum = target or pointers meet...      │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
import java.util.Arrays;

public class PairSum {
    public static int[] findPair(int[] arr, int target) {
        // Edge cases
        if (arr == null || arr.length < 2) {
            return new int[]{};
        }

        int left = 0;
        int right = arr.length - 1;

        // Move pointers toward each other
        while (left < right) {
            int sum = arr[left] + arr[right];
            
            if (sum == target) {
                return new int[]{arr[left], arr[right]};
            } else if (sum < target) {
                left++; // Need larger sum, move left pointer right
            } else {
                right--; // Need smaller sum, move right pointer left
            }
        }

        return new int[]{}; // No pair found
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5, 6, 7, 8, 9};
        int target = 10;
        
        System.out.println("Array: " + Arrays.toString(arr));
        System.out.println("Target: " + target);
        
        int[] result = findPair(arr, target);
        if (result.length == 2) {
            System.out.println("Pair found: [" + result[0] + ", " + result[1] + "]");
        } else {
            System.out.println("No pair found");
        }
        
        // Output:
        // Array: [1, 2, 3, 4, 5, 6, 7, 8, 9]
        // Target: 10
        // Pair found: [1, 9]
    }
}
```

### Time & Space Complexity
- **Time Complexity**: O(n) - We traverse the array once
- **Space Complexity**: O(1) - We use only a few variables

## 💡 Example 2: Remove Duplicates from Sorted Array (Same Direction)

### Problem Statement
Given a sorted array, remove duplicates in-place and return the new length.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  Array: [1, 1, 2, 2, 3, 4, 4, 5]                    │
│                                                       │
│  Initial: write → read →                              │
│  [1, 1, 2, 2, 3, 4, 4, 5]                           │
│                                                       │
│  Step 1: write → read →                               │
│  [1, 1, 2, 2, 3, 4, 4, 5] ← Copy 1                  │
│                                                       │
│  Step 2: write → read →                               │
│  [1, 1, 2, 2, 3, 4, 4, 5] ← Skip duplicate 1        │
│                                                       │
│  Step 3: write → read →                               │
│  [1, 2, 2, 2, 3, 4, 4, 5] ← Copy 2                  │
│                                                       │
│  Continue until end...                                │
│  Result: [1, 2, 3, 4, 5] (length 5)                 │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
public class RemoveDuplicates {
    public static int removeDuplicates(int[] arr) {
        if (arr == null || arr.length == 0) {
            return 0;
        }

        int write = 0; // Position to write unique elements
        int read = 1;  // Position to read elements

        // Move through array with two pointers
        while (read < arr.length) {
            if (arr[read] != arr[write]) {
                write++;
                arr[write] = arr[read];
            }
            read++;
        }

        return write + 1; // Length of new array
    }

    public static void main(String[] args) {
        int[] arr = {1, 1, 2, 2, 3, 4, 4, 5};
        
        System.out.println("Original array: " + java.util.Arrays.toString(arr));
        
        int newLength = removeDuplicates(arr);
        
        System.out.println("New length: " + newLength);
        System.out.print("Array after removing duplicates: [");
        for (int i = 0; i < newLength; i++) {
            System.out.print(arr[i]);
            if (i < newLength - 1) System.out.print(", ");
        }
        System.out.println("]");
        
        // Output:
        // Original array: [1, 1, 2, 2, 3, 4, 4, 5]
        // New length: 5
        // Array after removing duplicates: [1, 2, 3, 4, 5]
    }
}
```

## 💡 Example 3: Container With Most Water (Opposite Directions)

### Problem Statement
Given an array representing heights of walls, find two walls that can hold the maximum amount of water.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  Heights: [1, 8, 6, 2, 5, 4, 8, 3, 7]               │
│                                                       │
│  Initial: left → ← right                              │
│  [1, 8, 6, 2, 5, 4, 8, 3, 7]                        │
│  Water = min(1, 7) × (8-0) = 1 × 8 = 8              │
│                                                       │
│  Step 1: left → ← right                              │
│  [1, 8, 6, 2, 5, 4, 8, 3, 7]                        │
│  Water = min(8, 7) × (8-1) = 7 × 7 = 49             │
│                                                       │
│  Continue until pointers meet...                      │
│  Maximum water: 49                                    │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
public class ContainerWithMostWater {
    public static int maxArea(int[] height) {
        if (height == null || height.length < 2) {
            return 0;
        }

        int left = 0;
        int right = height.length - 1;
        int maxArea = 0;

        while (left < right) {
            // Calculate area with current walls
            int width = right - left;
            int h = Math.min(height[left], height[right]);
            int area = width * h;
            
            maxArea = Math.max(maxArea, area);

            // Move pointer with smaller height
            if (height[left] < height[right]) {
                left++;
            } else {
                right--;
            }
        }

        return maxArea;
    }

    public static void main(String[] args) {
        int[] height = {1, 8, 6, 2, 5, 4, 8, 3, 7};
        
        System.out.println("Heights: " + java.util.Arrays.toString(height));
        System.out.println("Maximum water area: " + maxArea(height));
        
        // Output:
        // Heights: [1, 8, 6, 2, 5, 4, 8, 3, 7]
        // Maximum water area: 49
    }
}
```

## 🎯 Common Patterns & Templates

### Template 1: Opposite Direction Pointers
```java
public int oppositePointers(int[] arr) {
    int left = 0;
    int right = arr.length - 1;
    
    while (left < right) {
        // Process elements at left and right
        if (condition) {
            left++;
        } else {
            right--;
        }
    }
    
    return result;
}
```

### Template 2: Same Direction Pointers
```java
public int sameDirectionPointers(int[] arr) {
    int slow = 0;
    int fast = 0;
    
    while (fast < arr.length) {
        // Process elements
        if (condition) {
            slow++;
        }
        fast++;
    }
    
    return result;
}
```

### Template 3: Fast and Slow Pointers
```java
public boolean fastSlowPointers(ListNode head) {
    ListNode slow = head;
    ListNode fast = head;
    
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
        
        if (slow == fast) {
            return true; // Cycle detected
        }
    }
    
    return false;
}
```

## 🚀 Practice Problems

### 🟢 Easy Level (5 Problems)
1. **[Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)** - Opposite direction pointers
2. **[Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)** - Same direction pointers
3. **[Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)** - Opposite direction with character checking
4. **[Move Zeroes](https://leetcode.com/problems/move-zeroes/)** - Same direction with swapping
5. **[Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/)** - Opposite direction with comparison

### 🟡 Medium Level (3 Problems)
1. **[Container With Most Water](https://leetcode.com/problems/container-with-most-water/)** - Opposite direction with area calculation
2. **[3Sum](https://leetcode.com/problems/3sum/)** - Fixed one pointer, two pointers for remaining
3. **[Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)** - Fast and slow pointers

### 🔴 Hard Level (2 Problems)
1. **[Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)** - Opposite direction with height tracking
2. **[Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)** - Multiple pointers approach

## 🎨 Key Takeaways

### ✅ Do's:
- Always check if array is sorted (if needed for opposite direction)
- Handle edge cases (null arrays, empty arrays, single element)
- Choose appropriate pointer movement strategy
- Consider space complexity (in-place vs extra space)

### ❌ Don'ts:
- Don't forget to move both pointers appropriately
- Don't assume array is sorted without checking
- Don't ignore edge cases with pointer boundaries
- Don't use two pointers when a single loop is sufficient

### 🧠 Memory Aids:
- **"Opposite directions for sorted arrays"**
- **"Same direction for in-place operations"**
- **"Fast and slow for cycles"**

## 🔍 Debugging Tips

1. **Print pointer positions** at each step to visualize movement
2. **Check boundary conditions** - when do pointers meet?
3. **Verify pointer movement logic** - are they moving correctly?
4. **Test with edge cases** - empty array, single element, all same values

## 📚 Further Reading

- [GeeksforGeeks - Two Pointers Technique](https://www.geeksforgeeks.org/two-pointers-technique/)
- [LeetCode - Two Pointers Problems](https://leetcode.com/tag/two-pointers/)

---

**🎉 Congratulations!** You've mastered the Two Pointers pattern. Practice with the problems above to solidify your understanding!

---

**[← Back to README](README.md)** | **[Next Pattern →](Fast_Slow_Pointers.markdown)**