# 📊 Arrays - The Foundation of Data Structures

## 📖 What is an Array?

Imagine a row of lockers in a school hallway, each numbered from 0 to n-1. You can store one item in each locker, and you can access any locker directly if you know its number. That's exactly what an **Array** is in programming!

An array is a collection of elements stored at contiguous memory locations. Each element can be accessed directly using an index.

```
┌─────────────────────────────────────────────────────────┐
│  Array Visualization                                   │
│                                                       │
│  Index:    0    1    2    3    4    5    6    7      │
│           ┌────┬────┬────┬────┬────┬────┬────┬────┐   │
│  Values:  │ 10 │ 20 │ 30 │ 40 │ 50 │ 60 │ 70 │ 80 │   │
│           └────┴────┴────┴────┴────┴────┴────┴────┘   │
│                                                       │
│  Memory:  [10][20][30][40][50][60][70][80]           │
│           ↑   ↑   ↑   ↑   ↑   ↑   ↑   ↑              │
│           Contiguous Memory Locations                 │
└─────────────────────────────────────────────────────────┘
```

## 🎯 Types of Arrays

### 1. Static Arrays
Fixed size, declared at compile time.

```java
int[] staticArray = new int[5]; // Fixed size of 5
```

### 2. Dynamic Arrays
Size can change at runtime (like ArrayList in Java).

```java
ArrayList<Integer> dynamicArray = new ArrayList<>();
```

## 🧠 Array Operations

### 1. Access (Read)
**Time Complexity**: O(1) - Constant time

```java
int value = arr[3]; // Access element at index 3
```

### 2. Search
**Time Complexity**: O(n) - Linear time

```java
public static int linearSearch(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == target) {
            return i; // Found at index i
        }
    }
    return -1; // Not found
}
```

### 3. Insertion
**Time Complexity**: O(n) - Linear time (due to shifting)

```java
public static void insertAt(int[] arr, int index, int value) {
    // Shift elements to make space
    for (int i = arr.length - 1; i > index; i--) {
        arr[i] = arr[i - 1];
    }
    arr[index] = value;
}
```

### 4. Deletion
**Time Complexity**: O(n) - Linear time (due to shifting)

```java
public static void deleteAt(int[] arr, int index) {
    // Shift elements to fill the gap
    for (int i = index; i < arr.length - 1; i++) {
        arr[i] = arr[i + 1];
    }
    arr[arr.length - 1] = 0; // Clear last element
}
```

## 💡 Example 1: Basic Array Operations

### Problem Statement
Demonstrate basic array operations: creation, access, modification, and traversal.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  Array Operations Demo                                 │
│                                                       │
│  Step 1: Create array                                 │
│  [0, 0, 0, 0, 0] ← Initialized with zeros            │
│                                                       │
│  Step 2: Insert values                                │
│  [10, 20, 30, 40, 50] ← After insertion              │
│                                                       │
│  Step 3: Access element                               │
│  arr[2] = 30 ← Direct access                          │
│                                                       │
│  Step 4: Modify element                               │
│  [10, 20, 35, 40, 50] ← After arr[2] = 35            │
│                                                       │
│  Step 5: Traverse array                               │
│  Print: 10 20 35 40 50                                │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
public class ArrayBasics {
    public static void main(String[] args) {
        // 1. Array Declaration and Initialization
        int[] arr = new int[5];
        
        // 2. Inserting elements
        arr[0] = 10;
        arr[1] = 20;
        arr[2] = 30;
        arr[3] = 40;
        arr[4] = 50;
        
        System.out.println("Array after insertion:");
        printArray(arr);
        
        // 3. Accessing elements
        System.out.println("Element at index 2: " + arr[2]);
        
        // 4. Modifying elements
        arr[2] = 35;
        System.out.println("Array after modification:");
        printArray(arr);
        
        // 5. Array length
        System.out.println("Array length: " + arr.length);
        
        // 6. Traversing array
        System.out.println("Traversing array:");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();
        
        // 7. Enhanced for loop
        System.out.println("Using enhanced for loop:");
        for (int element : arr) {
            System.out.print(element + " ");
        }
        System.out.println();
    }
    
    public static void printArray(int[] arr) {
        System.out.print("[");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i]);
            if (i < arr.length - 1) {
                System.out.print(", ");
            }
        }
        System.out.println("]");
    }
}
```

## 💡 Example 2: Dynamic Array (ArrayList)

### Problem Statement
Demonstrate dynamic array operations using ArrayList.

### Java Implementation

```java
import java.util.ArrayList;
import java.util.Arrays;

public class DynamicArrayDemo {
    public static void main(String[] args) {
        // 1. Create dynamic array
        ArrayList<Integer> dynamicArray = new ArrayList<>();
        
        // 2. Add elements (automatic resizing)
        dynamicArray.add(10);
        dynamicArray.add(20);
        dynamicArray.add(30);
        dynamicArray.add(40);
        dynamicArray.add(50);
        
        System.out.println("Dynamic array: " + dynamicArray);
        System.out.println("Size: " + dynamicArray.size());
        
        // 3. Insert at specific index
        dynamicArray.add(2, 25); // Insert 25 at index 2
        System.out.println("After insertion: " + dynamicArray);
        
        // 4. Remove element
        dynamicArray.remove(3); // Remove element at index 3
        System.out.println("After removal: " + dynamicArray);
        
        // 5. Check if element exists
        System.out.println("Contains 25: " + dynamicArray.contains(25));
        System.out.println("Contains 100: " + dynamicArray.contains(100));
        
        // 6. Get element at index
        System.out.println("Element at index 1: " + dynamicArray.get(1));
        
        // 7. Set element at index
        dynamicArray.set(1, 15);
        System.out.println("After setting: " + dynamicArray);
        
        // 8. Clear array
        dynamicArray.clear();
        System.out.println("After clearing: " + dynamicArray);
        System.out.println("Is empty: " + dynamicArray.isEmpty());
    }
}
```

## 💡 Example 3: Two-Dimensional Arrays

### Problem Statement
Demonstrate 2D array operations and matrix operations.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  2D Array (Matrix) Visualization                      │
│                                                       │
│  Row/Col:  0    1    2                               │
│         ┌─────┬─────┬─────┐                          │
│    0    │  1  │  2  │  3  │                          │
│         ├─────┼─────┼─────┤                          │
│    1    │  4  │  5  │  6  │                          │
│         ├─────┼─────┼─────┤                          │
│    2    │  7  │  8  │  9  │                          │
│         └─────┴─────┴─────┘                          │
│                                                       │
│  Access: matrix[row][column]                          │
│  Example: matrix[1][2] = 6                            │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
public class TwoDArrayDemo {
    public static void main(String[] args) {
        // 1. Create 2D array
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        
        System.out.println("2D Array:");
        printMatrix(matrix);
        
        // 2. Access element
        System.out.println("Element at [1][2]: " + matrix[1][2]);
        
        // 3. Modify element
        matrix[1][2] = 10;
        System.out.println("After modification:");
        printMatrix(matrix);
        
        // 4. Traverse 2D array
        System.out.println("Traversing by rows:");
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                System.out.print(matrix[i][j] + " ");
            }
            System.out.println();
        }
        
        // 5. Find sum of all elements
        int sum = 0;
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                sum += matrix[i][j];
            }
        }
        System.out.println("Sum of all elements: " + sum);
        
        // 6. Transpose matrix
        int[][] transpose = transposeMatrix(matrix);
        System.out.println("Transpose:");
        printMatrix(transpose);
    }
    
    public static void printMatrix(int[][] matrix) {
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                System.out.print(matrix[i][j] + " ");
            }
            System.out.println();
        }
        System.out.println();
    }
    
    public static int[][] transposeMatrix(int[][] matrix) {
        int rows = matrix.length;
        int cols = matrix[0].length;
        int[][] transpose = new int[cols][rows];
        
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                transpose[j][i] = matrix[i][j];
            }
        }
        
        return transpose;
    }
}
```

## 🎯 Common Array Patterns

### Pattern 1: Two Pointers
```java
public void twoPointers(int[] arr) {
    int left = 0;
    int right = arr.length - 1;
    
    while (left < right) {
        // Process elements at left and right
        left++;
        right--;
    }
}
```

### Pattern 2: Sliding Window
```java
public int slidingWindow(int[] arr, int k) {
    int windowSum = 0;
    
    // Calculate first window
    for (int i = 0; i < k; i++) {
        windowSum += arr[i];
    }
    
    int maxSum = windowSum;
    
    // Slide window
    for (int i = k; i < arr.length; i++) {
        windowSum = windowSum + arr[i] - arr[i - k];
        maxSum = Math.max(maxSum, windowSum);
    }
    
    return maxSum;
}
```

### Pattern 3: Prefix Sum
```java
public int[] prefixSum(int[] arr) {
    int[] prefix = new int[arr.length];
    prefix[0] = arr[0];
    
    for (int i = 1; i < arr.length; i++) {
        prefix[i] = prefix[i - 1] + arr[i];
    }
    
    return prefix;
}
```

## 🚀 Practice Problems

### 🟢 Easy Level (5 Problems)
1. **[Two Sum](https://leetcode.com/problems/two-sum/)** - Find pair with given sum
2. **[Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)** - In-place removal
3. **[Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)** - Single pass
4. **[Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)** - Kadane's algorithm
5. **[Move Zeroes](https://leetcode.com/problems/move-zeroes/)** - In-place operation

### 🟡 Medium Level (3 Problems)
1. **[3Sum](https://leetcode.com/problems/3sum/)** - Three pointer approach
2. **[Container With Most Water](https://leetcode.com/problems/container-with-most-water/)** - Two pointers
3. **[Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)** - Prefix/suffix product

### 🔴 Hard Level (2 Problems)
1. **[Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)** - Two pointers with height tracking
2. **[Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/)** - Binary search approach

## 🎨 Key Takeaways

### ✅ Do's:
- Always check array bounds before accessing
- Use appropriate data structure (static vs dynamic)
- Consider time and space complexity
- Handle edge cases (empty array, single element)

### ❌ Don'ts:
- Don't access array beyond its bounds
- Don't forget to initialize array elements
- Don't use arrays when other data structures are more appropriate
- Don't ignore memory constraints

### 🧠 Memory Aids:
- **"Index starts at 0"**
- **"Contiguous memory locations"**
- **"Direct access with index"**

## 🔍 Debugging Tips

1. **Check array bounds** - Always verify index is within range
2. **Print array contents** - Use helper methods to visualize
3. **Use debugger** - Step through array operations
4. **Test edge cases** - Empty array, single element, large arrays

## 📚 Further Reading

- [GeeksforGeeks - Arrays](https://www.geeksforgeeks.org/arrays/)
- [LeetCode - Array Problems](https://leetcode.com/tag/array/)

---

**🎉 Congratulations!** You've mastered Arrays. Practice with the problems above to solidify your understanding!

---

**[← Back to DSA Concepts](../README.md)** | **[Next Topic →](02 - Linked Lists.md)** 