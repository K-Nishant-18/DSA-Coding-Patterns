# 📚 Stacks: The LIFO Powerhouse

---

## 🚀 Why Learn Stacks?

Imagine a stack of books on your desk. You can only add a new book on top, and you can only remove the book from the top. You can't grab a book from the middle without moving the ones above it first! This is the magic of **stacks**—a fundamental data structure that follows the **LIFO (Last In, First Out)** principle.

Stacks are everywhere: browser back/forward buttons, undo/redo in text editors, function calls in programming, and even the way you organize your daily tasks. Mastering stacks unlocks your ability to solve a wide range of problems efficiently.

---

## 🧩 What is a Stack? (With Visuals)

A **stack** is a linear data structure that follows the **LIFO (Last In, First Out)** principle. Elements are added and removed from the same end, called the "top" of the stack.

### 📦 Analogy: A Stack of Plates

```
┌─────────────────────────────────────────────────────────┐
│  Stack Visualization                                   │
│                                                       │
│                    TOP                                 │
│                   ┌────┐                              │
│                   │ 40 │ ← Push/Pop from here         │
│                   ├────┤                              │
│                   │ 30 │                              │
│                   ├────┤                              │
│                   │ 20 │                              │
│                   ├────┤                              │
│                   │ 10 │                              │
│                   └────┘                              │
│                   BOTTOM                              │
│                                                       │
│  Operations:                                          │
│  • Push: Add element to top                           │
│  • Pop: Remove element from top                       │
│  • Peek: View top element without removing            │
└─────────────────────────────────────────────────────────┘
```

- Each **plate** represents an element
- You can only **add** plates on top
- You can only **remove** plates from the top
- The **top** is where all action happens
- The **bottom** is the first element added

### 🧠 Key Properties
- **LIFO Order**: Last element added is the first one removed
- **Single access point**: Only the top is accessible
- **Dynamic size**: Can grow and shrink as needed
- **Fast operations**: O(1) time for push, pop, and peek

### 💡 Real-World Examples
- Browser back/forward buttons
- Undo/redo functionality in applications
- Function call stack in programming
- Matching parentheses in expressions
- Depth-first search in graphs

---

## 🏷️ Types of Stacks

Stacks can be implemented in different ways! Let's explore the various types and their characteristics.

### 1. Array-Based Stack
- **Fixed size**: Uses a static array with a top pointer
- **Analogy**: A fixed-size bookshelf where you stack books

```
┌─────────────────────────────────────────────────────────┐
│  Array-Based Stack                                    │
│                                                       │
│  Array: [10, 20, 30, 40, _]                         │
│  Index:   0   1   2   3   4                          │
│  Top:     ↑                                          │
│          3 (points to top element)                    │
│                                                       │
│  Operations:                                          │
│  Push: Increment top, add element                     │
│  Pop: Return element, decrement top                   │
└─────────────────────────────────────────────────────────┘
```

### 2. Linked List-Based Stack
- **Dynamic size**: Uses a linked list with head as top
- **Analogy**: A chain of boxes where you add/remove from the front

```
┌─────────────────────────────────────────────────────────┐
│  Linked List-Based Stack                              │
│                                                       │
│  Top → [40|next] → [30|next] → [20|next] → [10|null] │
│         ↑                                            │
│       Head (top of stack)                            │
│                                                       │
│  Operations:                                          │
│  Push: Add new node at head                          │
│  Pop: Remove head node                               │
└─────────────────────────────────────────────────────────┘
```

### 3. Dynamic Array Stack
- **Auto-resizing**: Grows automatically when needed
- **Analogy**: A stretchy container that expands as you add items

```
┌─────────────────────────────────────────────────────────┐
│  Dynamic Array Stack                                  │
│                                                       │
│  Initial: [10, 20, 30] (size: 3)                    │
│  After push: [10, 20, 30, 40] (size: 4)             │
│  After push: [10, 20, 30, 40, 50] (size: 5)         │
│  Auto-expand: [10, 20, 30, 40, 50, _, _, _] (size: 8) │
└─────────────────────────────────────────────────────────┘
```

---

### ⚡ Quick Comparison Table

| Type              | Memory | Resize | Overflow | Use Case                    |
|-------------------|--------|--------|----------|----------------------------|
| Array-Based       | Fixed  | No     | Yes      | Known size requirements     |
| Linked List-Based | Dynamic| Yes    | No       | Unknown size requirements   |
| Dynamic Array     | Dynamic| Yes    | No       | General purpose             |

---

### 🕵️‍♂️ When to Use Which?
- **Array-Based**: When you know the maximum size in advance
- **Linked List-Based**: When you need dynamic sizing and memory efficiency
- **Dynamic Array**: When you want the best of both worlds (most common)

---

## 🛠️ Core Stack Operations (With Visuals & Code)

Stacks are powerful because of their simple but effective operations! Here are the most important operations, explained step by step.

---

### 1. Push
- **What?** Add an element to the top of the stack.
- **Analogy:** Adding a new plate on top of the stack.

```
Before Push:    After Push(50):
┌────┐         ┌────┐
│ 40 │         │ 50 │ ← New top
├────┤         ├────┤
│ 30 │         │ 40 │
├────┤         ├────┤
│ 20 │         │ 30 │
├────┤         ├────┤
│ 10 │         │ 20 │
└────┘         ├────┤
               │ 10 │
               └────┘
```

**Code:**
```java
public void push(int data) {
    if (isFull()) {
        System.out.println("Stack Overflow!");
        return;
    }
    arr[++top] = data;
}
```
```python
def push(self, data):
    if self.is_full():
        print("Stack Overflow!")
        return
    self.top += 1
    self.arr[self.top] = data
```
```cpp
void push(int data) {
    if (isFull()) {
        cout << "Stack Overflow!" << endl;
        return;
    }
    arr[++top] = data;
}
```

---

### 2. Pop
- **What?** Remove and return the top element from the stack.
- **Analogy:** Taking the top plate off the stack.

```
Before Pop:     After Pop():
┌────┐         ┌────┐
│ 50 │ ← Top   │ 40 │ ← New top
├────┤         ├────┤
│ 40 │         │ 30 │
├────┤         ├────┤
│ 30 │         │ 20 │
├────┤         ├────┤
│ 20 │         │ 10 │
├────┤         └────┘
│ 10 │
└────┘
Returns: 50
```

**Code:**
```java
public int pop() {
    if (isEmpty()) {
        System.out.println("Stack Underflow!");
        return -1;
    }
    return arr[top--];
}
```
```python
def pop(self):
    if self.is_empty():
        print("Stack Underflow!")
        return -1
    data = self.arr[self.top]
    self.top -= 1
    return data
```
```cpp
int pop() {
    if (isEmpty()) {
        cout << "Stack Underflow!" << endl;
        return -1;
    }
    return arr[top--];
}
```

---

### 3. Peek/Top
- **What?** View the top element without removing it.
- **Analogy:** Looking at the top plate without taking it.

```
Stack:          Peek Operation:
┌────┐         ┌────┐
│ 50 │ ← Top   │ 50 │ ← Just look, don't remove
├────┤         ├────┤
│ 40 │         │ 40 │
├────┤         ├────┤
│ 30 │         │ 30 │
├────┤         ├────┤
│ 20 │         │ 20 │
├────┤         ├────┤
│ 10 │         │ 10 │
└────┘         └────┘
Returns: 50    Stack unchanged
```

**Code:**
```java
public int peek() {
    if (isEmpty()) {
        System.out.println("Stack is empty!");
        return -1;
    }
    return arr[top];
}
```
```python
def peek(self):
    if self.is_empty():
        print("Stack is empty!")
        return -1
    return self.arr[self.top]
```
```cpp
int peek() {
    if (isEmpty()) {
        cout << "Stack is empty!" << endl;
        return -1;
    }
    return arr[top];
}
```

---

### 4. IsEmpty
- **What?** Check if the stack has no elements.
- **Analogy:** Checking if there are any plates on the stack.

```
Empty Stack:    Non-Empty Stack:
┌────┐         ┌────┐
│    │         │ 50 │
├────┤         ├────┤
│    │         │ 40 │
├────┤         ├────┤
│    │         │ 30 │
├────┤         ├────┤
│    │         │ 20 │
├────┤         ├────┤
│    │         │ 10 │
└────┘         └────┘
isEmpty: true   isEmpty: false
```

**Code:**
```java
public boolean isEmpty() {
    return top == -1;
}
```
```python
def is_empty(self):
    return self.top == -1
```
```cpp
bool isEmpty() {
    return top == -1;
}
```

---

### 5. Size
- **What?** Get the number of elements in the stack.
- **Analogy:** Counting how many plates are on the stack.

```
Stack:          Size Calculation:
┌────┐         ┌────┐
│ 50 │         │ 50 │ ← Element 4
├────┤         ├────┤
│ 40 │         │ 40 │ ← Element 3
├────┤         ├────┤
│ 30 │         │ 30 │ ← Element 2
├────┤         ├────┤
│ 20 │         │ 20 │ ← Element 1
├────┤         ├────┤
│ 10 │         │ 10 │ ← Element 0
└────┘         └────┘
Size: 5        Size = top + 1 = 4 + 1 = 5
```

**Code:**
```java
public int size() {
    return top + 1;
}
```
```python
def size(self):
    return self.top + 1
```
```cpp
int size() {
    return top + 1;
}
```

---

### ⏱️ Time Complexity Summary

| Operation | Time Complexity | Space Complexity |
|-----------|----------------|------------------|
| Push      | O(1)           | O(1)             |
| Pop       | O(1)           | O(1)             |
| Peek      | O(1)           | O(1)             |
| IsEmpty   | O(1)           | O(1)             |
| Size      | O(1)           | O(1)             |

---

## 🎯 Common Stack Patterns

### Pattern 1: Monotonic Stack
**Use case:** Finding next greater/smaller elements efficiently.

```
Array: [4, 5, 2, 10, 8]
Find next greater element for each:

Step 1: Process 4
Stack: [4] → Next greater: -1

Step 2: Process 5
Stack: [5] → Next greater: -1 (4 < 5, so 5 is next greater for 4)

Step 3: Process 2
Stack: [5, 2] → Next greater: -1

Step 4: Process 10
Stack: [10] → Next greater: -1 (10 > 2, 10 > 5)

Step 5: Process 8
Stack: [10, 8] → Next greater: 10
```

**Code:**
```java
public int[] nextGreaterElement(int[] nums) {
    int[] result = new int[nums.length];
    Stack<Integer> stack = new Stack<>();
    
    for (int i = nums.length - 1; i >= 0; i--) {
        while (!stack.isEmpty() && stack.peek() <= nums[i]) {
            stack.pop();
        }
        
        result[i] = stack.isEmpty() ? -1 : stack.peek();
        stack.push(nums[i]);
    }
    
    return result;
}
```

### Pattern 2: Parenthesis Matching
**Use case:** Validating balanced parentheses, brackets, and braces.

```
Expression: "((()))"
Process each character:

Step 1: '(' → Push to stack
Stack: ['(']

Step 2: '(' → Push to stack
Stack: ['(', '(']

Step 3: '(' → Push to stack
Stack: ['(', '(', '(']

Step 4: ')' → Pop from stack (matches)
Stack: ['(', '(']

Step 5: ')' → Pop from stack (matches)
Stack: ['(']

Step 6: ')' → Pop from stack (matches)
Stack: [] (empty)

Result: Valid parentheses!
```

**Code:**
```java
public boolean isValidParentheses(String s) {
    Stack<Character> stack = new Stack<>();
    
    for (char c : s.toCharArray()) {
        if (c == '(' || c == '{' || c == '[') {
            stack.push(c);
        } else if (c == ')' || c == '}' || c == ']') {
            if (stack.isEmpty()) {
                return false;
            }
            
            char top = stack.pop();
            if ((c == ')' && top != '(') ||
                (c == '}' && top != '{') ||
                (c == ']' && top != '[')) {
                return false;
            }
        }
    }
    
    return stack.isEmpty();
}
```

### Pattern 3: Postfix Expression Evaluation
**Use case:** Evaluating mathematical expressions in postfix notation.

```
Expression: "23*4+"
Process each character:

Step 1: '2' → Push to stack
Stack: [2]

Step 2: '3' → Push to stack
Stack: [2, 3]

Step 3: '*' → Pop 3, Pop 2, Push 2*3=6
Stack: [6]

Step 4: '4' → Push to stack
Stack: [6, 4]

Step 5: '+' → Pop 4, Pop 6, Push 6+4=10
Stack: [10]

Result: 10
```

**Code:**
```java
public int evaluatePostfix(String expression) {
    Stack<Integer> stack = new Stack<>();
    
    for (char c : expression.toCharArray()) {
        if (Character.isDigit(c)) {
            stack.push(c - '0');
        } else {
            int b = stack.pop();
            int a = stack.pop();
            
            switch (c) {
                case '+':
                    stack.push(a + b);
                    break;
                case '-':
                    stack.push(a - b);
                    break;
                case '*':
                    stack.push(a * b);
                    break;
                case '/':
                    stack.push(a / b);
                    break;
            }
        }
    }
    
    return stack.pop();
}
```

---

## 🐛 Debugging & Common Pitfalls

### ❌ Common Mistakes

1. **Stack Underflow**
   ```java
   // Bad: Popping from empty stack
   Stack<Integer> stack = new Stack<>();
   int value = stack.pop(); // Throws EmptyStackException
   
   // Good: Check before popping
   if (!stack.isEmpty()) {
       int value = stack.pop();
   }
   ```

2. **Stack Overflow (Array-based)**
   ```java
   // Bad: Pushing to full stack
   if (top >= capacity) {
       // Stack is full, can't push more
   }
   
   // Good: Check capacity before pushing
   if (top < capacity - 1) {
       arr[++top] = data;
   }
   ```

3. **Forgetting to Update Top Pointer**
   ```java
   // Bad: Incomplete push operation
   arr[top] = data; // Missing: top++
   
   // Good: Complete push operation
   arr[++top] = data;
   ```

### 🔧 Debugging Tips

1. **Print Stack Contents**
   ```java
   public void printStack() {
       System.out.print("Stack (top to bottom): ");
       for (int i = top; i >= 0; i--) {
           System.out.print(arr[i] + " ");
       }
       System.out.println();
   }
   ```

2. **Check Stack State**
   ```java
   System.out.println("Top: " + top);
   System.out.println("Size: " + size());
   System.out.println("Is Empty: " + isEmpty());
   System.out.println("Is Full: " + isFull());
   ```

3. **Use Debugger**
   - Set breakpoints in push/pop operations
   - Watch top pointer changes
   - Step through stack operations

---

## 🧠 Memory & Performance

### How Stacks Work in Memory

```
Memory Layout (Array-based):
┌─────────────────────────────────────────┐
│  Stack in Memory                       │
│                                       │
│  Base Address: 1000                   │
│  ┌────┬────┬────┬────┬────┐          │
│  │ 10 │ 20 │ 30 │ 40 │ 50 │          │
│  └────┴────┴────┴────┴────┘          │
│    ↑    ↑    ↑    ↑    ↑              │
│  1000 1004 1008 1012 1016            │
│                                       │
│  Top pointer: 4 (points to last element) │
└─────────────────────────────────────────┘
```

- **Contiguous memory**: Array-based stacks use consecutive memory
- **Fast access**: O(1) operations due to direct indexing
- **Memory efficient**: Only uses space for actual elements
- **Cache friendly**: Good spatial locality

### Performance Considerations

| Implementation | Push | Pop | Memory | Resize |
|----------------|------|-----|--------|--------|
| Array-based    | O(1) | O(1)| Fixed  | No     |
| Linked List    | O(1) | O(1)| Dynamic| Yes    |
| Dynamic Array  | O(1)*| O(1)| Dynamic| Yes    |

*Amortized O(1) for dynamic array

---

## 💡 Example 1: Basic Stack Operations

### Problem Statement
Demonstrate basic stack operations: push, pop, peek, and traversal.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  Stack Operations Demo                                 │
│                                                       │
│  Step 1: Create empty stack                           │
│  TOP → null                                           │
│                                                       │
│  Step 2: Push 10                                      │
│  TOP → [10]                                           │
│                                                       │
│  Step 3: Push 20                                      │
│  TOP → [20] → [10]                                    │
│                                                       │
│  Step 4: Push 30                                      │
│  TOP → [30] → [20] → [10]                             │
│                                                       │
│  Step 5: Peek (view top)                              │
│  Peek: 30 (stack unchanged)                           │
│                                                       │
│  Step 6: Pop (remove top)                             │
│  Pop: 30, TOP → [20] → [10]                           │
│                                                       │
│  Step 7: Pop again                                    │
│  Pop: 20, TOP → [10]                                  │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
import java.util.Stack;

public class StackBasics {
    public static void main(String[] args) {
        // Using Java's built-in Stack
        Stack<Integer> stack = new Stack<>();
        
        System.out.println("=== Stack Operations Demo ===");
        
        // Push operations
        System.out.println("Pushing elements...");
        stack.push(10);
        System.out.println("Pushed: 10, Stack: " + stack);
        
        stack.push(20);
        System.out.println("Pushed: 20, Stack: " + stack);
        
        stack.push(30);
        System.out.println("Pushed: 30, Stack: " + stack);
        
        stack.push(40);
        System.out.println("Pushed: 40, Stack: " + stack);
        
        // Peek operation
        System.out.println("\nPeek (view top): " + stack.peek());
        System.out.println("Stack after peek: " + stack);
        
        // Pop operations
        System.out.println("\nPopping elements...");
        System.out.println("Popped: " + stack.pop() + ", Stack: " + stack);
        System.out.println("Popped: " + stack.pop() + ", Stack: " + stack);
        System.out.println("Popped: " + stack.pop() + ", Stack: " + stack);
        System.out.println("Popped: " + stack.pop() + ", Stack: " + stack);
        
        // Check if empty
        System.out.println("\nIs stack empty? " + stack.isEmpty());
        
        // Try to pop from empty stack
        System.out.println("Trying to pop from empty stack...");
        if (!stack.isEmpty()) {
            stack.pop();
        } else {
            System.out.println("Cannot pop from empty stack!");
        }
        
        // Stack size
        System.out.println("Stack size: " + stack.size());
    }
}
```

---

## 💡 Example 2: Custom Stack Implementation

### Problem Statement
Implement a custom stack with additional features like searching and displaying.

### Java Implementation

```java
public class CustomStack {
    private int[] arr;
    private int top;
    private int capacity;
    
    public CustomStack(int size) {
        arr = new int[size];
        capacity = size;
        top = -1;
    }
    
    // Push operation
    public void push(int data) {
        if (isFull()) {
            System.out.println("Stack Overflow! Cannot push " + data);
            return;
        }
        arr[++top] = data;
        System.out.println("Pushed: " + data);
    }
    
    // Pop operation
    public int pop() {
        if (isEmpty()) {
            System.out.println("Stack Underflow! Cannot pop");
            return -1;
        }
        int data = arr[top--];
        System.out.println("Popped: " + data);
        return data;
    }
    
    // Peek operation
    public int peek() {
        if (isEmpty()) {
            System.out.println("Stack is empty! Cannot peek");
            return -1;
        }
        return arr[top];
    }
    
    // Check if stack is empty
    public boolean isEmpty() {
        return top == -1;
    }
    
    // Check if stack is full
    public boolean isFull() {
        return top == capacity - 1;
    }
    
    // Get stack size
    public int size() {
        return top + 1;
    }
    
    // Search for an element
    public int search(int element) {
        for (int i = top; i >= 0; i--) {
            if (arr[i] == element) {
                return top - i + 1; // Position from top (1-based)
            }
        }
        return -1; // Element not found
    }
    
    // Display stack
    public void display() {
        if (isEmpty()) {
            System.out.println("Stack is empty!");
            return;
        }
        
        System.out.print("Stack (top to bottom): ");
        for (int i = top; i >= 0; i--) {
            System.out.print(arr[i]);
            if (i > 0) {
                System.out.print(" → ");
            }
        }
        System.out.println();
    }
    
    // Clear stack
    public void clear() {
        top = -1;
        System.out.println("Stack cleared!");
    }
    
    public static void main(String[] args) {
        CustomStack stack = new CustomStack(5);
        
        System.out.println("=== Custom Stack Demo ===");
        
        // Push operations
        stack.push(10);
        stack.push(20);
        stack.push(30);
        stack.push(40);
        stack.push(50);
        
        // Try to push when full
        stack.push(60);
        
        // Display stack
        stack.display();
        
        // Search operations
        System.out.println("\nSearching for elements:");
        System.out.println("Position of 30: " + stack.search(30) + " from top");
        System.out.println("Position of 100: " + stack.search(100) + " (not found)");
        
        // Peek operation
        System.out.println("\nPeek: " + stack.peek());
        
        // Pop operations
        System.out.println("\nPopping elements:");
        stack.pop();
        stack.pop();
        stack.pop();
        
        // Display after popping
        stack.display();
        
        // Stack information
        System.out.println("\nStack Info:");
        System.out.println("Size: " + stack.size());
        System.out.println("Is empty: " + stack.isEmpty());
        System.out.println("Is full: " + stack.isFull());
        
        // Clear stack
        stack.clear();
        stack.display();
    }
}
```

---

## 💡 Example 3: Stack Applications

### Problem Statement
Demonstrate common applications of stacks: parenthesis matching, postfix evaluation, and function call stack.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  Parenthesis Matching                                 │
│                                                       │
│  Expression: "((()))"                                 │
│                                                       │
│  Step 1: '(' → Push to stack                          │
│  Stack: ['(']                                         │
│                                                       │
│  Step 2: '(' → Push to stack                          │
│  Stack: ['(', '(']                                    │
│                                                       │
│  Step 3: '(' → Push to stack                          │
│  Stack: ['(', '(', '(']                               │
│                                                       │
│  Step 4: ')' → Pop from stack (matches)               │
│  Stack: ['(', '(']                                    │
│                                                       │
│  Step 5: ')' → Pop from stack (matches)               │
│  Stack: ['(']                                         │
│                                                       │
│  Step 6: ')' → Pop from stack (matches)               │
│  Stack: [] (empty)                                    │
│                                                       │
│  Result: Valid parentheses!                           │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
import java.util.Stack;

public class StackApplications {
    
    // 1. Parenthesis Matching
    public static boolean isValidParentheses(String s) {
        Stack<Character> stack = new Stack<>();
        
        for (char c : s.toCharArray()) {
            if (c == '(' || c == '{' || c == '[') {
                stack.push(c);
            } else if (c == ')' || c == '}' || c == ']') {
                if (stack.isEmpty()) {
                    return false;
                }
                
                char top = stack.pop();
                if ((c == ')' && top != '(') ||
                    (c == '}' && top != '{') ||
                    (c == ']' && top != '[')) {
                    return false;
                }
            }
        }
        
        return stack.isEmpty();
    }
    
    // 2. Postfix Expression Evaluation
    public static int evaluatePostfix(String expression) {
        Stack<Integer> stack = new Stack<>();
        
        for (char c : expression.toCharArray()) {
            if (Character.isDigit(c)) {
                stack.push(c - '0');
            } else {
                int b = stack.pop();
                int a = stack.pop();
                
                switch (c) {
                    case '+':
                        stack.push(a + b);
                        break;
                    case '-':
                        stack.push(a - b);
                        break;
                    case '*':
                        stack.push(a * b);
                        break;
                    case '/':
                        stack.push(a / b);
                        break;
                }
            }
        }
        
        return stack.pop();
    }
    
    // 3. Reverse String using Stack
    public static String reverseString(String str) {
        Stack<Character> stack = new Stack<>();
        
        // Push all characters to stack
        for (char c : str.toCharArray()) {
            stack.push(c);
        }
        
        // Pop characters to get reversed string
        StringBuilder reversed = new StringBuilder();
        while (!stack.isEmpty()) {
            reversed.append(stack.pop());
        }
        
        return reversed.toString();
    }
    
    // 4. Decimal to Binary Conversion
    public static String decimalToBinary(int decimal) {
        Stack<Integer> stack = new Stack<>();
        
        if (decimal == 0) {
            return "0";
        }
        
        while (decimal > 0) {
            stack.push(decimal % 2);
            decimal /= 2;
        }
        
        StringBuilder binary = new StringBuilder();
        while (!stack.isEmpty()) {
            binary.append(stack.pop());
        }
        
        return binary.toString();
    }
    
    public static void main(String[] args) {
        System.out.println("=== Stack Applications Demo ===");
        
        // 1. Parenthesis Matching
        String[] expressions = {"((()))", "({[]})", "(((", ")))", "([)]"};
        System.out.println("\n1. Parenthesis Matching:");
        for (String expr : expressions) {
            System.out.println("'" + expr + "' is valid: " + isValidParentheses(expr));
        }
        
        // 2. Postfix Evaluation
        String postfix = "23*4+";
        System.out.println("\n2. Postfix Evaluation:");
        System.out.println("Expression: " + postfix);
        System.out.println("Result: " + evaluatePostfix(postfix));
        
        // 3. String Reversal
        String text = "Hello World";
        System.out.println("\n3. String Reversal:");
        System.out.println("Original: " + text);
        System.out.println("Reversed: " + reverseString(text));
        
        // 4. Decimal to Binary
        int decimal = 25;
        System.out.println("\n4. Decimal to Binary Conversion:");
        System.out.println("Decimal: " + decimal);
        System.out.println("Binary: " + decimalToBinary(decimal));
    }
}
```

---

## 🚀 Practice Problems

### 🟢 Easy Level (10 Problems)
1. **[Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)** - Stack for matching
2. **[Min Stack](https://leetcode.com/problems/min-stack/)** - Stack with minimum tracking
3. **[Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/)** - Queue implementation
4. **[Backspace String Compare](https://leetcode.com/problems/backspace-string-compare/)** - Stack simulation
5. **[Remove All Adjacent Duplicates In String](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/)** - Stack for duplicates
6. **[Make The String Great](https://leetcode.com/problems/make-the-string-great/)** - Stack for string cleaning
7. **[Remove Outermost Parentheses](https://leetcode.com/problems/remove-outermost-parentheses/)** - Stack for parsing
8. **[Crawler Log Folder](https://leetcode.com/problems/crawler-log-folder/)** - Stack simulation
9. **[Maximum Nesting Depth of the Parentheses](https://leetcode.com/problems/maximum-nesting-depth-of-the-parentheses/)** - Stack depth tracking
10. **[Check If Word Is Valid After Substitutions](https://leetcode.com/problems/check-if-word-is-valid-after-substitutions/)** - Stack validation

### 🟡 Medium Level (10 Problems)
1. **[Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/)** - Postfix evaluation
2. **[Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/)** - Monotonic stack
3. **[Asteroid Collision](https://leetcode.com/problems/asteroid-collision/)** - Stack simulation
4. **[Daily Temperatures](https://leetcode.com/problems/daily-temperatures/)** - Monotonic stack
5. **[Online Stock Span](https://leetcode.com/problems/online-stock-span/)** - Monotonic stack
6. **[Simplify Path](https://leetcode.com/problems/simplify-path/)** - Stack for path processing
7. **[Decode String](https://leetcode.com/problems/decode-string/)** - Stack for nested decoding
8. **[Basic Calculator II](https://leetcode.com/problems/basic-calculator-ii/)** - Expression evaluation
9. **[Remove K Digits](https://leetcode.com/problems/remove-k-digits/)** - Monotonic stack
10. **[132 Pattern](https://leetcode.com/problems/132-pattern/)** - Monotonic stack

### 🔴 Hard Level (5 Problems)
1. **[Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/)** - Monotonic stack
2. **[Basic Calculator](https://leetcode.com/problems/basic-calculator/)** - Expression evaluation
3. **[Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)** - Stack approach
4. **[Longest Valid Parentheses](https://leetcode.com/problems/longest-valid-parentheses/)** - Stack with indices
5. **[Remove Duplicate Letters](https://leetcode.com/problems/remove-duplicate-letters/)** - Monotonic stack

---

## 🎨 Key Takeaways

### ✅ Do's:
- Always check if stack is empty before popping
- Use stack for LIFO operations (undo, backtracking)
- Consider using stack for parenthesis matching
- Use monotonic stack for next greater/smaller element problems
- Handle stack overflow/underflow gracefully
- Use appropriate stack implementation for your needs

### ❌ Don'ts:
- Don't try to access middle elements directly
- Don't forget to check for empty stack before operations
- Don't use stack when you need random access
- Don't ignore the LIFO principle
- Don't forget to handle edge cases (empty stack, single element)
- Don't use stack for FIFO operations (use queue instead)

### 🧠 Memory Aids:
- **"Last In, First Out (LIFO)"**
- **"Stack of plates"**
- **"Push to add, Pop to remove"**
- **"Only top is accessible"**
- **"Check empty before pop"**

---

## 🔍 Debugging Tips

1. **Check stack state** - Always verify if stack is empty before operations
2. **Print stack contents** - Use helper methods to visualize
3. **Use debugger** - Step through push/pop operations
4. **Test with edge cases** - Empty stack, single element, full stack
5. **Validate input** - Check for null or invalid inputs
6. **Monitor stack size** - Track stack growth and capacity

---

## 📚 Further Reading

- [GeeksforGeeks - Stack Data Structure](https://www.geeksforgeeks.org/stack-data-structure/)
- [LeetCode - Stack Problems](https://leetcode.com/tag/stack/)
- [HackerRank - Stack Problems](https://www.hackerrank.com/domains/data-structures?filters%5Bsubdomains%5D%5B%5D=stacks)
- [Codeforces - Stack Problems](https://codeforces.com/problemset?tags=stacks)

---

**🎉 Congratulations!** You've mastered Stacks. Practice with the problems above to solidify your understanding!

---

**[← Back to DSA Concepts](../README.md)** | **[Previous Topic →](02 - Linked Lists.md)** | **[Next Topic →](04 - Queues.md)** 