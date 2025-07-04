# 🪟 Sliding Window Pattern

## 📖 What is Sliding Window?

Imagine you're looking through a window at a beautiful landscape. You can only see a portion of the view at any given time, but you can slide the window to see different parts. That's exactly what the **Sliding Window** pattern does in programming!

The Sliding Window pattern is a technique where we maintain a "window" (a range of elements) that slides through an array or string to solve problems efficiently.

```
┌─────────────────────────────────────────────────────────┐
│  Array: [1, 4, 2, 10, 2, 3, 1, 0, 20]              │
│                                                       │
│  Window Size = 4                                      │
│                                                       │
│  [1, 4, 2, 10] ← First window                        │
│     [4, 2, 10, 2] ← Sliding...                      │
│        [2, 10, 2, 3] ← Sliding...                   │
│           [10, 2, 3, 1] ← Sliding...                │
│              [2, 3, 1, 0] ← Sliding...              │
│                 [3, 1, 0, 20] ← Last window         │
└─────────────────────────────────────────────────────────┘
```

## 🎯 When to Use Sliding Window?

### ✅ Perfect for:
- **Fixed-size problems**: "Find maximum sum of subarray of size K"
- **Variable-size problems**: "Find longest substring with at most K distinct characters"
- **Contiguous subarrays/substrings**: Problems involving consecutive elements
- **Optimization problems**: Finding min/max values in a range

### ❌ Not suitable for:
- Non-contiguous elements
- Problems requiring all possible combinations
- When elements can be in any order

## 🧠 How Does It Work?

### The Two-Pointer Approach

```
┌─────────────────────────────────────────────────────────┐
│  Two Pointers: start and end                          │
│                                                       │
│  start ←→ end                                         │
│   ↓                                                    │
│  [1, 4, 2, 10, 2, 3, 1, 0, 20]                      │
│                                                       │
│  Step 1: Expand window (move end)                     │
│  start ←→ end                                         │
│   ↓     ↓                                             │
│  [1, 4, 2, 10, 2, 3, 1, 0, 20]                      │
│                                                       │
│  Step 2: Shrink window (move start) if needed        │
│     start ←→ end                                      │
│      ↓     ↓                                          │
│  [1, 4, 2, 10, 2, 3, 1, 0, 20]                      │
└─────────────────────────────────────────────────────────┘
```

### The Algorithm Steps:

1. **Initialize**: Set start = 0, end = 0
2. **Expand**: Move end pointer to include new elements
3. **Process**: Calculate/update your result
4. **Shrink**: Move start pointer if condition is violated
5. **Repeat**: Continue until end reaches the end

## 📊 Types of Sliding Windows

### 1. Fixed-Size Window
Window size remains constant throughout the process.

```
┌─────────────────────────────────────────────────────────┐
│  Fixed Window Size = 3                                │
│                                                       │
│  [1, 4, 2] ← Window 1                               │
│     [4, 2, 10] ← Window 2                           │
│        [2, 10, 2] ← Window 3                        │
│           [10, 2, 3] ← Window 4                     │
│              [2, 3, 1] ← Window 5                   │
│                 [3, 1, 0] ← Window 6                │
│                    [1, 0, 20] ← Window 7            │
└─────────────────────────────────────────────────────────┘
```

### 2. Variable-Size Window
Window size changes based on conditions.

```
┌─────────────────────────────────────────────────────────┐
│  Variable Window (e.g., sum ≤ target)                │
│                                                       │
│  [1] ← Small window                                  │
│  [1, 4] ← Growing...                                │
│  [1, 4, 2] ← Growing...                             │
│  [1, 4, 2, 10] ← Too big! Shrink...                │
│     [4, 2, 10] ← Still too big...                   │
│        [2, 10] ← Perfect!                           │
└─────────────────────────────────────────────────────────┘
```

## 💡 Example 1: Maximum Sum Subarray of Size K

### Problem Statement
Given an array of integers and a number K, find the maximum sum of any contiguous subarray of size K.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  Array: [1, 4, 2, 10, 2, 3, 1, 0, 20]              │
│  K = 4                                                │
│                                                       │
│  Step 1: Calculate first window sum                   │
│  [1, 4, 2, 10] = 1 + 4 + 2 + 10 = 17               │
│                                                       │
│  Step 2: Slide window                                │
│  [1, 4, 2, 10, 2]                                   │
│  Remove 1, Add 2: 17 - 1 + 2 = 18                   │
│                                                       │
│  Step 3: Continue sliding...                         │
│  [4, 2, 10, 2] = 18                                 │
│  [2, 10, 2, 3] = 18 - 4 + 3 = 17                   │
│  [10, 2, 3, 1] = 17 - 2 + 1 = 16                   │
│  [2, 3, 1, 0] = 16 - 10 + 0 = 6                    │
│  [3, 1, 0, 20] = 6 - 2 + 20 = 24 ← Maximum!        │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
public class MaxSumSubarray {
    public static int findMaxSumSubarray(int[] arr, int k) {
        // Edge cases
        if (arr == null || k <= 0 || k > arr.length) {
            throw new IllegalArgumentException("Invalid input");
        }

        // Step 1: Calculate sum of first window
        int windowSum = 0;
        for (int i = 0; i < k; i++) {
            windowSum += arr[i];
        }
        
        int maxSum = windowSum; // Initialize with first window

        // Step 2: Slide the window
        for (int i = k; i < arr.length; i++) {
            // Add new element, remove old element
            windowSum = windowSum + arr[i] - arr[i - k];
            maxSum = Math.max(maxSum, windowSum);
        }

        return maxSum;
    }

    public static void main(String[] args) {
        int[] arr = {1, 4, 2, 10, 2, 3, 1, 0, 20};
        int k = 4;
        
        System.out.println("Array: " + java.util.Arrays.toString(arr));
        System.out.println("Window size: " + k);
        System.out.println("Maximum sum: " + findMaxSumSubarray(arr, k));
        
        // Output:
        // Array: [1, 4, 2, 10, 2, 3, 1, 0, 20]
        // Window size: 4
        // Maximum sum: 24
    }
}
```

### Time & Space Complexity
- **Time Complexity**: O(n) - We traverse the array only once
- **Space Complexity**: O(1) - We use only a few variables

## 💡 Example 2: Longest Substring with At Most K Distinct Characters

### Problem Statement
Given a string, find the length of the longest substring that contains at most K distinct characters.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  String: "eceba"  K = 2                              │
│                                                       │
│  Step 1: [e] ← Start with 'e'                        │
│  Step 2: [ec] ← Add 'c' (2 distinct)                │
│  Step 3: [ece] ← Add 'e' (still 2 distinct)         │
│  Step 4: [eceb] ← Add 'b' (3 distinct - too many!)  │
│  Step 5: [ceb] ← Remove 'e' from start              │
│  Step 6: [ceba] ← Add 'a' (3 distinct - too many!)  │
│  Step 7: [eba] ← Remove 'c' from start              │
│                                                       │
│  Longest substring: "ece" (length 3)                 │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
import java.util.*;

public class LongestSubstringKDistinct {
    public static int lengthOfLongestSubstringKDistinct(String s, int k) {
        if (s == null || s.length() == 0 || k == 0) {
            return 0;
        }

        Map<Character, Integer> charCount = new HashMap<>();
        int start = 0;
        int maxLength = 0;

        // Expand window with end pointer
        for (int end = 0; end < s.length(); end++) {
            char currentChar = s.charAt(end);
            
            // Add current character to window
            charCount.put(currentChar, charCount.getOrDefault(currentChar, 0) + 1);

            // Shrink window if we have too many distinct characters
            while (charCount.size() > k) {
                char startChar = s.charAt(start);
                charCount.put(startChar, charCount.get(startChar) - 1);
                
                if (charCount.get(startChar) == 0) {
                    charCount.remove(startChar);
                }
                start++;
            }

            // Update max length
            maxLength = Math.max(maxLength, end - start + 1);
        }

        return maxLength;
    }

    public static void main(String[] args) {
        String s = "eceba";
        int k = 2;
        
        System.out.println("String: \"" + s + "\"");
        System.out.println("K: " + k);
        System.out.println("Longest substring length: " + 
                         lengthOfLongestSubstringKDistinct(s, k));
        
        // Output:
        // String: "eceba"
        // K: 2
        // Longest substring length: 3
    }
}
```

## 🎯 Common Patterns & Templates

### Template 1: Fixed-Size Window
```java
public int fixedSizeWindow(int[] arr, int k) {
    int windowSum = 0;
    
    // Calculate first window
    for (int i = 0; i < k; i++) {
        windowSum += arr[i];
    }
    
    int result = windowSum;
    
    // Slide window
    for (int i = k; i < arr.length; i++) {
        windowSum = windowSum + arr[i] - arr[i - k];
        result = Math.max(result, windowSum); // or Math.min()
    }
    
    return result;
}
```

### Template 2: Variable-Size Window
```java
public int variableSizeWindow(int[] arr, int target) {
    int start = 0;
    int currentSum = 0;
    int result = 0;
    
    for (int end = 0; end < arr.length; end++) {
        currentSum += arr[end];
        
        // Shrink window if condition violated
        while (currentSum > target) {
            currentSum -= arr[start];
            start++;
        }
        
        result = Math.max(result, end - start + 1);
    }
    
    return result;
}
```

## 🚀 Practice Problems

### Easy Level
- [Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/)
- [Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)

### Medium Level
- [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
- [Longest Substring with At Most K Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/)
- [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)

### Hard Level
- [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)
- [Longest Substring with At Most Two Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-two-distinct-characters/)

## 🎨 Key Takeaways

### ✅ Do's:
- Always handle edge cases (null arrays, empty strings, invalid K values)
- Use appropriate data structures (HashMap for character counting, Deque for max/min)
- Think about the window expansion and contraction logic
- Consider both fixed-size and variable-size scenarios

### ❌ Don'ts:
- Don't recalculate window contents from scratch each time
- Don't forget to update your result at each step
- Don't ignore the shrinking condition
- Don't assume the window always grows

### 🧠 Memory Aids:
- **"Expand to grow, shrink when needed"**
- **"Add new, remove old"** (for fixed-size windows)
- **"Two pointers dance together"**

## 🔍 Debugging Tips

1. **Print the window at each step** to visualize the process
2. **Track your pointers** (start, end) and window contents
3. **Verify edge cases** (empty input, single element, etc.)
4. **Check your termination condition** - when does the loop end?

## 📚 Further Reading

- [GeeksforGeeks - Sliding Window Technique](https://www.geeksforgeeks.org/window-sliding-technique/)
- [LeetCode - Sliding Window Problems](https://leetcode.com/tag/sliding-window/)

---

**🎉 Congratulations!** You've mastered the Sliding Window pattern. Practice with the problems above to solidify your understanding!

---

**[← Back to README](README.md)** | **[Next Pattern →](Two_Pointers.markdown)**