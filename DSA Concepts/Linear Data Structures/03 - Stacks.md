# 📚 Stacks - LIFO Data Structure

## 📖 What is a Stack?

Imagine a stack of plates at a buffet. You can only add a new plate on top of the stack, and you can only remove the plate from the top. You can't take a plate from the middle or bottom without removing the ones above it first. That's exactly what a **Stack** is in programming!

A stack is a linear data structure that follows the **LIFO (Last In, First Out)** principle. Elements are added and removed from the same end, called the "top" of the stack.

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

## 🎯 Stack Operations

### 1. Push
Add an element to the top of the stack.
**Time Complexity**: O(1) - Constant time

### 2. Pop
Remove and return the top element from the stack.
**Time Complexity**: O(1) - Constant time

### 3. Peek/Top
View the top element without removing it.
**Time Complexity**: O(1) - Constant time

### 4. IsEmpty
Check if the stack is empty.
**Time Complexity**: O(1) - Constant time

### 5. Size
Get the number of elements in the stack.
**Time Complexity**: O(1) - Constant time

## 🧠 Stack Implementation

### Using Array
```java
public class StackArray {
    private int[] arr;
    private int top;
    private int capacity;
    
    public StackArray(int size) {
        arr = new int[size];
        capacity = size;
        top = -1;
    }
    
    public void push(int data) {
        if (isFull()) {
            System.out.println("Stack Overflow!");
            return;
        }
        arr[++top] = data;
    }
    
    public int pop() {
        if (isEmpty()) {
            System.out.println("Stack Underflow!");
            return -1;
        }
        return arr[top--];
    }
    
    public int peek() {
        if (isEmpty()) {
            System.out.println("Stack is empty!");
            return -1;
        }
        return arr[top];
    }
    
    public boolean isEmpty() {
        return top == -1;
    }
    
    public boolean isFull() {
        return top == capacity - 1;
    }
    
    public int size() {
        return top + 1;
    }
}
```

### Using Linked List
```java
class StackNode {
    int data;
    StackNode next;
    
    StackNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class StackLinkedList {
    private StackNode top;
    
    public StackLinkedList() {
        this.top = null;
    }
    
    public void push(int data) {
        StackNode newNode = new StackNode(data);
        newNode.next = top;
        top = newNode;
    }
    
    public int pop() {
        if (isEmpty()) {
            System.out.println("Stack Underflow!");
            return -1;
        }
        int data = top.data;
        top = top.next;
        return data;
    }
    
    public int peek() {
        if (isEmpty()) {
            System.out.println("Stack is empty!");
            return -1;
        }
        return top.data;
    }
    
    public boolean isEmpty() {
        return top == null;
    }
}
```

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

## 🎯 Common Stack Patterns

### Pattern 1: Monotonic Stack
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

### Pattern 2: Stack for DFS
```java
public void dfsIterative(Node root) {
    if (root == null) return;
    
    Stack<Node> stack = new Stack<>();
    stack.push(root);
    
    while (!stack.isEmpty()) {
        Node current = stack.pop();
        System.out.print(current.val + " ");
        
        if (current.right != null) {
            stack.push(current.right);
        }
        if (current.left != null) {
            stack.push(current.left);
        }
    }
}
```

### Pattern 3: Stack for Expression Evaluation
```java
public int evaluateExpression(String expression) {
    Stack<Integer> numbers = new Stack<>();
    Stack<Character> operators = new Stack<>();
    
    for (char c : expression.toCharArray()) {
        if (Character.isDigit(c)) {
            numbers.push(c - '0');
        } else if (c == '(') {
            operators.push(c);
        } else if (c == ')') {
            while (operators.peek() != '(') {
                applyOperation(numbers, operators.pop());
            }
            operators.pop(); // Remove '('
        } else {
            while (!operators.isEmpty() && precedence(operators.peek()) >= precedence(c)) {
                applyOperation(numbers, operators.pop());
            }
            operators.push(c);
        }
    }
    
    while (!operators.isEmpty()) {
        applyOperation(numbers, operators.pop());
    }
    
    return numbers.pop();
}
```

## 🚀 Practice Problems

### 🟢 Easy Level (5 Problems)
1. **[Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)** - Stack for matching
2. **[Min Stack](https://leetcode.com/problems/min-stack/)** - Stack with minimum tracking
3. **[Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/)** - Queue implementation
4. **[Backspace String Compare](https://leetcode.com/problems/backspace-string-compare/)** - Stack simulation
5. **[Remove All Adjacent Duplicates In String](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/)** - Stack for duplicates

### 🟡 Medium Level (3 Problems)
1. **[Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/)** - Postfix evaluation
2. **[Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/)** - Monotonic stack
3. **[Asteroid Collision](https://leetcode.com/problems/asteroid-collision/)** - Stack simulation

### 🔴 Hard Level (2 Problems)
1. **[Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/)** - Monotonic stack
2. **[Basic Calculator](https://leetcode.com/problems/basic-calculator/)** - Expression evaluation

## 🎨 Key Takeaways

### ✅ Do's:
- Always check if stack is empty before popping
- Use stack for LIFO operations (undo, backtracking)
- Consider using stack for parenthesis matching
- Use monotonic stack for next greater/smaller element problems

### ❌ Don'ts:
- Don't try to access middle elements directly
- Don't forget to handle stack overflow/underflow
- Don't use stack when you need random access
- Don't ignore the LIFO principle

### 🧠 Memory Aids:
- **"Last In, First Out (LIFO)"**
- **"Stack of plates"**
- **"Push to add, Pop to remove"**

## 🔍 Debugging Tips

1. **Print stack contents** - Use helper methods to visualize
2. **Check for empty stack** - Always verify before popping
3. **Use debugger** - Step through push/pop operations
4. **Test with edge cases** - Empty stack, single element, full stack

## 📚 Further Reading

- [GeeksforGeeks - Stack Data Structure](https://www.geeksforgeeks.org/stack-data-structure/)
- [LeetCode - Stack Problems](https://leetcode.com/tag/stack/)

---

**🎉 Congratulations!** You've mastered Stacks. Practice with the problems above to solidify your understanding!

---

**[← Back to DSA Concepts](../README.md)** | **[Previous Topic →](02 - Linked Lists.md)** | **[Next Topic →](04 - Queues.md)** 