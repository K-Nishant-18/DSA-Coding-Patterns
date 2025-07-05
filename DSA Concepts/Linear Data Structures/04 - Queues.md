# 🚶 Queues: The FIFO Foundation

---

## 🚀 Why Learn Queues?

Imagine standing in line at your favorite coffee shop. The first person who joined the line gets served first, and new people join at the end. You can't cut in the middle or serve someone from the back—that's exactly what a **queue** is in programming!

Queues are everywhere: task scheduling in operating systems, print job management, breadth-first search in graphs, and even the way you organize your daily tasks. Mastering queues unlocks your ability to build efficient systems that process data in order.

---

## 🧩 What is a Queue? (With Visuals)

A **queue** is a linear data structure that follows the **FIFO (First In, First Out)** principle. Elements are added at one end (rear) and removed from the other end (front).

### 📦 Analogy: A Line of People

```
┌─────────────────────────────────────────────────────────┐
│  Queue Visualization                                   │
│                                                       │
│  FRONT ← [10] → [20] → [30] → [40] ← REAR            │
│           ↑              ↑              ↑              │
│         Dequeue        Middle        Enqueue          │
│         (Remove)       Elements      (Add)            │
│                                                       │
│  Operations:                                          │
│  • Enqueue: Add element at rear                       │
│  • Dequeue: Remove element from front                 │
│  • Peek: View front element without removing          │
│  • Front: First element in queue                      │
│  • Rear: Last element in queue                        │
└─────────────────────────────────────────────────────────┘
```

- Each **person** represents an element
- **Front** is where people get served (dequeue)
- **Rear** is where new people join (enqueue)
- **FIFO Order**: First person in line gets served first
- **No cutting**: You can't access middle elements directly

### 🧠 Key Properties
- **FIFO Order**: First element added is the first one removed
- **Two access points**: Front for removal, rear for addition
- **Dynamic size**: Can grow and shrink as needed
- **Fast operations**: O(1) time for enqueue, dequeue, and peek

### 💡 Real-World Examples
- Print job queue in office
- Task scheduling in operating systems
- Breadth-first search in graphs
- Customer service call center
- Order processing in e-commerce

---

## 🏷️ Types of Queues

Queues come in different flavors! Let's explore the various types and their characteristics.

### 1. Simple Queue (Linear Queue)
- **Basic FIFO**: Standard queue with enqueue and dequeue
- **Analogy**: A simple line of people at a store

```
┌─────────────────────────────────────────────────────────┐
│  Simple Queue                                         │
│                                                       │
│  FRONT → [10] → [20] → [30] → [40] ← REAR            │
│                                                       │
│  Operations:                                          │
│  Enqueue: Add at rear                                 │
│  Dequeue: Remove from front                           │
│  Peek: View front element                             │
└─────────────────────────────────────────────────────────┘
```

### 2. Circular Queue
- **Fixed size**: Reuses space when elements are dequeued
- **Analogy**: A circular conveyor belt that reuses positions

```
┌─────────────────────────────────────────────────────────┐
│  Circular Queue                                       │
│                                                       │
│  Array: [10, 20, 30, 40, 50]                        │
│  Index:   0   1   2   3   4                          │
│  Front: 1, Rear: 4                                   │
│                                                       │
│  After dequeue: [null, 20, 30, 40, 50]               │
│  Front: 2, Rear: 4                                   │
│                                                       │
│  After enqueue 60: [60, null, 30, 40, 50]            │
│  Front: 2, Rear: 0 (wrapped around)                  │
└─────────────────────────────────────────────────────────┘
```

### 3. Priority Queue
- **Priority-based**: Elements dequeued by priority, not FIFO
- **Analogy**: Emergency room where critical patients go first

```
┌─────────────────────────────────────────────────────────┐
│  Priority Queue (Min-Heap)                            │
│                                                       │
│        10 (highest priority)                          │
│       /  \                                            │
│     20    30                                          │
│    /  \                                               │
│   40   50                                             │
│                                                       │
│  Dequeue order: 10 → 20 → 30 → 40 → 50               │
└─────────────────────────────────────────────────────────┘
```

### 4. Double-Ended Queue (Deque)
- **Both ends**: Can add/remove from front and rear
- **Analogy**: A line where people can join or leave from either end

```
┌─────────────────────────────────────────────────────────┐
│  Double-Ended Queue                                   │
│                                                       │
│  FRONT ← [10] → [20] → [30] → [40] ← REAR            │
│           ↑              ↑              ↑              │
│         Add/Remove    Middle        Add/Remove        │
│         from front    Elements      from rear         │
│                                                       │
│  Operations:                                          │
│  • addFirst(), removeFirst()                          │
│  • addLast(), removeLast()                            │
│  • peekFirst(), peekLast()                            │
└─────────────────────────────────────────────────────────┘
```

---

### ⚡ Quick Comparison Table

| Type           | Access Points | Priority | Size      | Use Case                    |
|----------------|---------------|----------|-----------|----------------------------|
| Simple Queue   | Front/Rear    | FIFO     | Dynamic   | Basic FIFO operations       |
| Circular Queue | Front/Rear    | FIFO     | Fixed     | Fixed-size scenarios        |
| Priority Queue | Front         | Priority | Dynamic   | Priority-based processing    |
| Deque          | Both ends     | FIFO     | Dynamic   | Flexible access patterns    |

---

### 🕵️‍♂️ When to Use Which?
- **Simple Queue**: For basic FIFO operations
- **Circular Queue**: When you have fixed memory constraints
- **Priority Queue**: When order matters (emergency systems, task scheduling)
- **Deque**: When you need flexibility in adding/removing from both ends

---

## 🛠️ Core Queue Operations (With Visuals & Code)

Queues are powerful because of their simple but effective operations! Here are the most important operations, explained step by step.

---

### 1. Enqueue
- **What?** Add an element to the rear of the queue.
- **Analogy:** A new person joining the end of the line.

```
Before Enqueue:    After Enqueue(50):
FRONT → [10] → [20] → [30] ← REAR
                    ↑
                  New rear

FRONT → [10] → [20] → [30] → [50] ← REAR
```

**Code:**
```java
public void enqueue(int data) {
    if (isFull()) {
        System.out.println("Queue Overflow!");
        return;
    }
    rear = (rear + 1) % capacity;
    arr[rear] = data;
    size++;
}
```
```python
def enqueue(self, data):
    if self.is_full():
        print("Queue Overflow!")
        return
    self.rear = (self.rear + 1) % self.capacity
    self.arr[self.rear] = data
    self.size += 1
```
```cpp
void enqueue(int data) {
    if (isFull()) {
        cout << "Queue Overflow!" << endl;
        return;
    }
    rear = (rear + 1) % capacity;
    arr[rear] = data;
    size++;
}
```

---

### 2. Dequeue
- **What?** Remove and return the element from the front of the queue.
- **Analogy:** The first person in line getting served and leaving.

```
Before Dequeue:    After Dequeue():
FRONT → [10] → [20] → [30] → [50] ← REAR
         ↑
       Remove this

FRONT → [20] → [30] → [50] ← REAR
         ↑
       New front
Returns: 10
```

**Code:**
```java
public int dequeue() {
    if (isEmpty()) {
        System.out.println("Queue Underflow!");
        return -1;
    }
    int data = arr[front];
    front = (front + 1) % capacity;
    size--;
    return data;
}
```
```python
def dequeue(self):
    if self.is_empty():
        print("Queue Underflow!")
        return -1
    data = self.arr[self.front]
    self.front = (self.front + 1) % self.capacity
    self.size -= 1
    return data
```
```cpp
int dequeue() {
    if (isEmpty()) {
        cout << "Queue Underflow!" << endl;
        return -1;
    }
    int data = arr[front];
    front = (front + 1) % capacity;
    size--;
    return data;
}
```

---

### 3. Peek/Front
- **What?** View the front element without removing it.
- **Analogy:** Looking at who's next in line without serving them.

```
Queue:              Peek Operation:
FRONT → [10] → [20] → [30] → [50] ← REAR
         ↑
       Just look, don't remove

Returns: 10 (queue unchanged)
```

**Code:**
```java
public int peek() {
    if (isEmpty()) {
        System.out.println("Queue is empty!");
        return -1;
    }
    return arr[front];
}
```
```python
def peek(self):
    if self.is_empty():
        print("Queue is empty!")
        return -1
    return self.arr[self.front]
```
```cpp
int peek() {
    if (isEmpty()) {
        cout << "Queue is empty!" << endl;
        return -1;
    }
    return arr[front];
}
```

---

### 4. IsEmpty
- **What?** Check if the queue has no elements.
- **Analogy:** Checking if there's anyone in line.

```
Empty Queue:        Non-Empty Queue:
FRONT → null ← REAR FRONT → [10] → [20] → [30] ← REAR

isEmpty: true       isEmpty: false
```

**Code:**
```java
public boolean isEmpty() {
    return size == 0;
}
```
```python
def is_empty(self):
    return self.size == 0
```
```cpp
bool isEmpty() {
    return size == 0;
}
```

---

### 5. Size
- **What?** Get the number of elements in the queue.
- **Analogy:** Counting how many people are in line.

```
Queue:              Size Calculation:
FRONT → [10] → [20] → [30] → [50] ← REAR
         ↑              ↑              ↑
       Element 1    Element 2    Element 3
Size: 4
```

**Code:**
```java
public int size() {
    return size;
}
```
```python
def size(self):
    return self.size
```
```cpp
int size() {
    return size;
}
```

---

### ⏱️ Time Complexity Summary

| Operation | Time Complexity | Space Complexity |
|-----------|----------------|------------------|
| Enqueue   | O(1)           | O(1)             |
| Dequeue   | O(1)           | O(1)             |
| Peek      | O(1)           | O(1)             |
| IsEmpty   | O(1)           | O(1)             |
| Size      | O(1)           | O(1)             |

---

## 🎯 Common Queue Patterns

### Pattern 1: Queue for BFS (Breadth-First Search)
**Use case:** Level-order traversal, shortest path problems.

```
Tree:                BFS Order:
     1                Level 0: [1]
   /   \              Level 1: [2, 3]
  2     3             Level 2: [4, 5, 6, 7]
 / \   / \
4   5 6   7

Queue: [1] → [2,3] → [3,4,5] → [4,5,6,7] → [5,6,7] → [6,7] → [7] → []
```

**Code:**
```java
public void bfs(Node root) {
    if (root == null) return;
    
    Queue<Node> queue = new LinkedList<>();
    queue.offer(root);
    
    while (!queue.isEmpty()) {
        Node current = queue.poll();
        System.out.print(current.val + " ");
        
        if (current.left != null) {
            queue.offer(current.left);
        }
        if (current.right != null) {
            queue.offer(current.right);
        }
    }
}
```

### Pattern 2: Sliding Window with Queue
**Use case:** Finding maximum/minimum in sliding windows.

```
Array: [1, 3, -1, -3, 5, 3, 6, 7], k = 3
Window: [1,3,-1] → [3,-1,-3] → [-1,-3,5] → [-3,5,3] → [5,3,6] → [3,6,7]
Max:   [3] → [3] → [5] → [5] → [6] → [7]
```

**Code:**
```java
public int[] maxSlidingWindow(int[] nums, int k) {
    if (nums == null || k <= 0) return new int[0];
    
    int n = nums.length;
    int[] result = new int[n - k + 1];
    Deque<Integer> deque = new LinkedList<>();
    
    for (int i = 0; i < n; i++) {
        // Remove elements outside window
        while (!deque.isEmpty() && deque.peek() < i - k + 1) {
            deque.poll();
        }
        
        // Remove smaller elements
        while (!deque.isEmpty() && nums[deque.peekLast()] < nums[i]) {
            deque.pollLast();
        }
        
        deque.offer(i);
        
        if (i >= k - 1) {
            result[i - k + 1] = nums[deque.peek()];
        }
    }
    
    return result;
}
```

### Pattern 3: Queue for Level Order Traversal
**Use case:** Processing tree nodes level by level.

```
Tree:                Level Order:
     1               Level 0: [1]
   /   \             Level 1: [2, 3]
  2     3            Level 2: [4, 5, 6, 7]
 / \   / \
4   5 6   7

Result: [[1], [2,3], [4,5,6,7]]
```

**Code:**
```java
public List<List<Integer>> levelOrder(TreeNode root) {
    List<List<Integer>> result = new ArrayList<>();
    if (root == null) return result;
    
    Queue<TreeNode> queue = new LinkedList<>();
    queue.offer(root);
    
    while (!queue.isEmpty()) {
        int levelSize = queue.size();
        List<Integer> level = new ArrayList<>();
        
        for (int i = 0; i < levelSize; i++) {
            TreeNode current = queue.poll();
            level.add(current.val);
            
            if (current.left != null) {
                queue.offer(current.left);
            }
            if (current.right != null) {
                queue.offer(current.right);
            }
        }
        
        result.add(level);
    }
    
    return result;
}
```

---

## 🐛 Debugging & Common Pitfalls

### ❌ Common Mistakes

1. **Queue Underflow**
   ```java
   // Bad: Dequeuing from empty queue
   Queue<Integer> queue = new LinkedList<>();
   int value = queue.poll(); // Returns null
   
   // Good: Check before dequeuing
   if (!queue.isEmpty()) {
       int value = queue.poll();
   }
   ```

2. **Queue Overflow (Array-based)**
   ```java
   // Bad: Enqueuing to full queue
   if (size >= capacity) {
       // Queue is full, can't enqueue more
   }
   
   // Good: Check capacity before enqueuing
   if (size < capacity) {
       rear = (rear + 1) % capacity;
       arr[rear] = data;
       size++;
   }
   ```

3. **Forgetting to Update Size**
   ```java
   // Bad: Incomplete enqueue operation
   arr[rear] = data; // Missing: size++
   
   // Good: Complete enqueue operation
   arr[rear] = data;
   size++;
   ```

### 🔧 Debugging Tips

1. **Print Queue Contents**
   ```java
   public void printQueue() {
       System.out.print("Queue (front to rear): ");
       for (int i = 0; i < size; i++) {
           int index = (front + i) % capacity;
           System.out.print(arr[index] + " ");
       }
       System.out.println();
   }
   ```

2. **Check Queue State**
   ```java
   System.out.println("Front: " + front);
   System.out.println("Rear: " + rear);
   System.out.println("Size: " + size);
   System.out.println("Is Empty: " + isEmpty());
   System.out.println("Is Full: " + isFull());
   ```

3. **Use Debugger**
   - Set breakpoints in enqueue/dequeue operations
   - Watch front and rear pointers
   - Step through queue operations

---

## 🧠 Memory & Performance

### How Queues Work in Memory

```
Memory Layout (Array-based):
┌─────────────────────────────────────────┐
│  Queue in Memory                       │
│                                       │
│  Base Address: 1000                   │
│  ┌────┬────┬────┬────┬────┐          │
│  │ 10 │ 20 │ 30 │ 40 │ 50 │          │
│  └────┴────┴────┴────┴────┘          │
│    ↑    ↑    ↑    ↑    ↑              │
│  1000 1004 1008 1012 1016            │
│                                       │
│  Front pointer: 0 (points to first element) │
│  Rear pointer: 4 (points to last element)   │
└─────────────────────────────────────────┘
```

- **Contiguous memory**: Array-based queues use consecutive memory
- **Fast access**: O(1) operations due to direct indexing
- **Memory efficient**: Only uses space for actual elements
- **Circular reuse**: Efficient space utilization in circular queues

### Performance Considerations

| Implementation | Enqueue | Dequeue | Memory | Resize |
|----------------|---------|---------|--------|--------|
| Array-based    | O(1)    | O(1)    | Fixed  | No     |
| Linked List    | O(1)    | O(1)    | Dynamic| Yes    |
| Circular Array | O(1)    | O(1)    | Fixed  | No     |

---

## 💡 Example 1: Basic Queue Operations

### Problem Statement
Demonstrate basic queue operations: enqueue, dequeue, peek, and traversal.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  Queue Operations Demo                                 │
│                                                       │
│  Step 1: Create empty queue                           │
│  FRONT → null ← REAR                                  │
│                                                       │
│  Step 2: Enqueue 10                                   │
│  FRONT → [10] ← REAR                                  │
│                                                       │
│  Step 3: Enqueue 20                                   │
│  FRONT → [10] → [20] ← REAR                           │
│                                                       │
│  Step 4: Enqueue 30                                   │
│  FRONT → [10] → [20] → [30] ← REAR                    │
│                                                       │
│  Step 5: Peek (view front)                            │
│  Peek: 10 (queue unchanged)                           │
│                                                       │
│  Step 6: Dequeue (remove front)                       │
│  Dequeue: 10, FRONT → [20] → [30] ← REAR              │
│                                                       │
│  Step 7: Dequeue again                                │
│  Dequeue: 20, FRONT → [30] ← REAR                     │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
import java.util.LinkedList;
import java.util.Queue;

public class QueueBasics {
    public static void main(String[] args) {
        // Using Java's built-in Queue (LinkedList implementation)
        Queue<Integer> queue = new LinkedList<>();
        
        System.out.println("=== Queue Operations Demo ===");
        
        // Enqueue operations
        System.out.println("Enqueuing elements...");
        queue.offer(10);
        System.out.println("Enqueued: 10, Queue: " + queue);
        
        queue.offer(20);
        System.out.println("Enqueued: 20, Queue: " + queue);
        
        queue.offer(30);
        System.out.println("Enqueued: 30, Queue: " + queue);
        
        queue.offer(40);
        System.out.println("Enqueued: 40, Queue: " + queue);
        
        // Peek operation
        System.out.println("\nPeek (view front): " + queue.peek());
        System.out.println("Queue after peek: " + queue);
        
        // Dequeue operations
        System.out.println("\nDequeuing elements...");
        System.out.println("Dequeued: " + queue.poll() + ", Queue: " + queue);
        System.out.println("Dequeued: " + queue.poll() + ", Queue: " + queue);
        System.out.println("Dequeued: " + queue.poll() + ", Queue: " + queue);
        System.out.println("Dequeued: " + queue.poll() + ", Queue: " + queue);
        
        // Check if empty
        System.out.println("\nIs queue empty? " + queue.isEmpty());
        
        // Try to dequeue from empty queue
        System.out.println("Trying to dequeue from empty queue...");
        Integer result = queue.poll();
        System.out.println("Dequeue result: " + result);
        
        // Queue size
        System.out.println("Queue size: " + queue.size());
    }
}
```

---

## 💡 Example 2: Custom Queue Implementation

### Problem Statement
Implement a custom queue with additional features like searching and displaying.

### Java Implementation

```java
public class CustomQueue {
    private int[] arr;
    private int front;
    private int rear;
    private int size;
    private int capacity;
    
    public CustomQueue(int size) {
        arr = new int[size];
        capacity = size;
        front = 0;
        rear = -1;
        this.size = 0;
    }
    
    // Enqueue operation
    public void enqueue(int data) {
        if (isFull()) {
            System.out.println("Queue Overflow! Cannot enqueue " + data);
            return;
        }
        rear = (rear + 1) % capacity;
        arr[rear] = data;
        size++;
        System.out.println("Enqueued: " + data);
    }
    
    // Dequeue operation
    public int dequeue() {
        if (isEmpty()) {
            System.out.println("Queue Underflow! Cannot dequeue");
            return -1;
        }
        int data = arr[front];
        front = (front + 1) % capacity;
        size--;
        System.out.println("Dequeued: " + data);
        return data;
    }
    
    // Peek operation
    public int peek() {
        if (isEmpty()) {
            System.out.println("Queue is empty! Cannot peek");
            return -1;
        }
        return arr[front];
    }
    
    // Check if queue is empty
    public boolean isEmpty() {
        return size == 0;
    }
    
    // Check if queue is full
    public boolean isFull() {
        return size == capacity;
    }
    
    // Get queue size
    public int getSize() {
        return size;
    }
    
    // Get front element
    public int getFront() {
        if (isEmpty()) {
            System.out.println("Queue is empty!");
            return -1;
        }
        return arr[front];
    }
    
    // Get rear element
    public int getRear() {
        if (isEmpty()) {
            System.out.println("Queue is empty!");
            return -1;
        }
        return arr[rear];
    }
    
    // Search for an element
    public int search(int element) {
        if (isEmpty()) {
            return -1;
        }
        
        for (int i = 0; i < size; i++) {
            int index = (front + i) % capacity;
            if (arr[index] == element) {
                return i + 1; // Position from front (1-based)
            }
        }
        return -1; // Element not found
    }
    
    // Display queue
    public void display() {
        if (isEmpty()) {
            System.out.println("Queue is empty!");
            return;
        }
        
        System.out.print("Queue (front to rear): ");
        for (int i = 0; i < size; i++) {
            int index = (front + i) % capacity;
            System.out.print(arr[index]);
            if (i < size - 1) {
                System.out.print(" → ");
            }
        }
        System.out.println();
    }
    
    // Clear queue
    public void clear() {
        front = 0;
        rear = -1;
        size = 0;
        System.out.println("Queue cleared!");
    }
    
    public static void main(String[] args) {
        CustomQueue queue = new CustomQueue(5);
        
        System.out.println("=== Custom Queue Demo ===");
        
        // Enqueue operations
        queue.enqueue(10);
        queue.enqueue(20);
        queue.enqueue(30);
        queue.enqueue(40);
        queue.enqueue(50);
        
        // Try to enqueue when full
        queue.enqueue(60);
        
        // Display queue
        queue.display();
        
        // Search operations
        System.out.println("\nSearching for elements:");
        System.out.println("Position of 30: " + queue.search(30) + " from front");
        System.out.println("Position of 100: " + queue.search(100) + " (not found)");
        
        // Peek operation
        System.out.println("\nPeek: " + queue.peek());
        
        // Dequeue operations
        System.out.println("\nDequeuing elements:");
        queue.dequeue();
        queue.dequeue();
        queue.dequeue();
        
        // Display after dequeuing
        queue.display();
        
        // Queue information
        System.out.println("\nQueue Info:");
        System.out.println("Size: " + queue.getSize());
        System.out.println("Front: " + queue.getFront());
        System.out.println("Rear: " + queue.getRear());
        System.out.println("Is empty: " + queue.isEmpty());
        System.out.println("Is full: " + queue.isFull());
        
        // Clear queue
        queue.clear();
        queue.display();
    }
}
```

---

## 💡 Example 3: Circular Queue Implementation

### Problem Statement
Implement a circular queue that efficiently reuses space.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  Circular Queue Operations                             │
│                                                       │
│  Initial: [null, null, null, null, null]              │
│  Front: 0, Rear: -1                                   │
│                                                       │
│  After enqueue 10: [10, null, null, null, null]       │
│  Front: 0, Rear: 0                                    │
│                                                       │
│  After enqueue 20: [10, 20, null, null, null]         │
│  Front: 0, Rear: 1                                    │
│                                                       │
│  After dequeue: [null, 20, null, null, null]          │
│  Front: 1, Rear: 1                                    │
│                                                       │
│  After enqueue 30: [null, 20, 30, null, null]         │
│  Front: 1, Rear: 2                                    │
│                                                       │
│  After enqueue 40, 50: [null, 20, 30, 40, 50]         │
│  Front: 1, Rear: 4                                    │
│                                                       │
│  After dequeue: [null, null, 30, 40, 50]              │
│  Front: 2, Rear: 4                                    │
│                                                       │
│  After enqueue 60: [60, null, 30, 40, 50]             │
│  Front: 2, Rear: 0 (wrapped around)                   │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
public class CircularQueue {
    private int[] arr;
    private int front;
    private int rear;
    private int size;
    private int capacity;
    
    public CircularQueue(int size) {
        arr = new int[size];
        capacity = size;
        front = 0;
        rear = -1;
        this.size = 0;
    }
    
    // Enqueue operation
    public boolean enqueue(int data) {
        if (isFull()) {
            System.out.println("Queue is full! Cannot enqueue " + data);
            return false;
        }
        
        rear = (rear + 1) % capacity;
        arr[rear] = data;
        size++;
        System.out.println("Enqueued: " + data);
        return true;
    }
    
    // Dequeue operation
    public int dequeue() {
        if (isEmpty()) {
            System.out.println("Queue is empty! Cannot dequeue");
            return -1;
        }
        
        int data = arr[front];
        front = (front + 1) % capacity;
        size--;
        System.out.println("Dequeued: " + data);
        return data;
    }
    
    // Peek operation
    public int peek() {
        if (isEmpty()) {
            System.out.println("Queue is empty! Cannot peek");
            return -1;
        }
        return arr[front];
    }
    
    // Check if queue is empty
    public boolean isEmpty() {
        return size == 0;
    }
    
    // Check if queue is full
    public boolean isFull() {
        return size == capacity;
    }
    
    // Get queue size
    public int getSize() {
        return size;
    }
    
    // Display circular queue
    public void display() {
        if (isEmpty()) {
            System.out.println("Queue is empty!");
            return;
        }
        
        System.out.print("Circular Queue: ");
        for (int i = 0; i < size; i++) {
            int index = (front + i) % capacity;
            System.out.print(arr[index]);
            if (i < size - 1) {
                System.out.print(" → ");
            }
        }
        System.out.println();
        
        System.out.println("Front: " + front + ", Rear: " + rear + ", Size: " + size);
    }
    
    public static void main(String[] args) {
        CircularQueue queue = new CircularQueue(5);
        
        System.out.println("=== Circular Queue Demo ===");
        
        // Enqueue operations
        queue.enqueue(10);
        queue.enqueue(20);
        queue.enqueue(30);
        queue.enqueue(40);
        queue.enqueue(50);
        
        // Try to enqueue when full
        queue.enqueue(60);
        
        // Display queue
        queue.display();
        
        // Dequeue operations
        System.out.println("\nDequeuing elements:");
        queue.dequeue();
        queue.dequeue();
        
        // Display after dequeuing
        queue.display();
        
        // Enqueue more elements (circular behavior)
        System.out.println("\nEnqueuing more elements:");
        queue.enqueue(60);
        queue.enqueue(70);
        
        // Display final state
        queue.display();
        
        // Queue information
        System.out.println("\nQueue Info:");
        System.out.println("Size: " + queue.getSize());
        System.out.println("Is empty: " + queue.isEmpty());
        System.out.println("Is full: " + queue.isFull());
    }
}
```

---

## 💡 Example 4: Priority Queue Implementation

### Problem Statement
Implement a priority queue where elements are dequeued based on priority.

### Java Implementation

```java
import java.util.PriorityQueue;

public class PriorityQueueDemo {
    public static void main(String[] args) {
        // Using Java's built-in PriorityQueue (min-heap by default)
        PriorityQueue<Integer> minPQ = new PriorityQueue<>();
        
        System.out.println("=== Min Priority Queue Demo ===");
        
        // Add elements
        minPQ.offer(30);
        minPQ.offer(10);
        minPQ.offer(50);
        minPQ.offer(20);
        minPQ.offer(40);
        
        System.out.println("Priority Queue: " + minPQ);
        System.out.println("Size: " + minPQ.size());
        
        // Remove elements (always removes minimum)
        System.out.println("\nRemoving elements (minimum first):");
        while (!minPQ.isEmpty()) {
            System.out.println("Removed: " + minPQ.poll());
        }
        
        // Max Priority Queue (using reverse order)
        PriorityQueue<Integer> maxPQ = new PriorityQueue<>((a, b) -> b - a);
        
        System.out.println("\n=== Max Priority Queue Demo ===");
        
        // Add elements
        maxPQ.offer(30);
        maxPQ.offer(10);
        maxPQ.offer(50);
        maxPQ.offer(20);
        maxPQ.offer(40);
        
        System.out.println("Max Priority Queue: " + maxPQ);
        
        // Remove elements (always removes maximum)
        System.out.println("\nRemoving elements (maximum first):");
        while (!maxPQ.isEmpty()) {
            System.out.println("Removed: " + maxPQ.poll());
        }
        
        // Custom Priority Queue with objects
        PriorityQueue<Person> personPQ = new PriorityQueue<>((p1, p2) -> p1.age - p2.age);
        
        System.out.println("\n=== Custom Priority Queue Demo ===");
        
        personPQ.offer(new Person("Alice", 25));
        personPQ.offer(new Person("Bob", 30));
        personPQ.offer(new Person("Charlie", 20));
        personPQ.offer(new Person("David", 35));
        
        System.out.println("Person Priority Queue (by age):");
        while (!personPQ.isEmpty()) {
            Person p = personPQ.poll();
            System.out.println("Name: " + p.name + ", Age: " + p.age);
        }
    }
    
    static class Person {
        String name;
        int age;
        
        Person(String name, int age) {
            this.name = name;
            this.age = age;
        }
    }
}
```

---

## 🚀 Practice Problems

### 🟢 Easy Level (10 Problems)
1. **[Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/)** - Stack implementation
2. **[Number of Recent Calls](https://leetcode.com/problems/number-of-recent-calls/)** - Sliding window with queue
3. **[Moving Average from Data Stream](https://leetcode.com/problems/moving-average-from-data-stream/)** - Queue for sliding window
4. **[Design Circular Queue](https://leetcode.com/problems/design-circular-queue/)** - Circular queue implementation
5. **[Design Circular Deque](https://leetcode.com/problems/design-circular-deque/)** - Double-ended queue
6. **[Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/)** - Queue implementation
7. **[First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/)** - Queue for tracking
8. **[Logger Rate Limiter](https://leetcode.com/problems/logger-rate-limiter/)** - Queue for rate limiting
9. **[Design Hit Counter](https://leetcode.com/problems/design-hit-counter/)** - Queue for hit counting
10. **[Design Phone Directory](https://leetcode.com/problems/design-phone-directory/)** - Queue for resource management

### 🟡 Medium Level (10 Problems)
1. **[Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)** - Monotonic queue
2. **[Open the Lock](https://leetcode.com/problems/open-the-lock/)** - BFS with queue
3. **[Perfect Squares](https://leetcode.com/problems/perfect-squares/)** - BFS approach
4. **[Rotting Oranges](https://leetcode.com/problems/rotting-oranges/)** - BFS with queue
5. **[01 Matrix](https://leetcode.com/problems/01-matrix/)** - BFS for distance
6. **[As Far from Land as Possible](https://leetcode.com/problems/as-far-from-land-as-possible/)** - BFS optimization
7. **[Shortest Path in Binary Matrix](https://leetcode.com/problems/shortest-path-in-binary-matrix/)** - BFS pathfinding
8. **[Snakes and Ladders](https://leetcode.com/problems/snakes-and-ladders/)** - BFS game simulation
9. **[Jump Game III](https://leetcode.com/problems/jump-game-iii/)** - BFS with queue
10. **[Reach a Number](https://leetcode.com/problems/reach-a-number/)** - BFS approach

### 🔴 Hard Level (5 Problems)
1. **[Word Ladder](https://leetcode.com/problems/word-ladder/)** - BFS with queue
2. **[Word Ladder II](https://leetcode.com/problems/word-ladder-ii/)** - BFS with path tracking
3. **[Shortest Path to Get All Keys](https://leetcode.com/problems/shortest-path-to-get-all-keys/)** - BFS with state
4. **[Minimum Moves to Reach Target with Rotations](https://leetcode.com/problems/minimum-moves-to-reach-target-with-rotations/)** - BFS with complex state
5. **[Escape a Large Maze](https://leetcode.com/problems/escape-a-large-maze/)** - BFS optimization

---

## 🎨 Key Takeaways

### ✅ Do's:
- Always check if queue is empty before dequeuing
- Use queue for FIFO operations (BFS, task scheduling)
- Consider circular queue for fixed-size scenarios
- Use priority queue when order matters
- Handle queue overflow/underflow gracefully
- Use appropriate queue implementation for your needs

### ❌ Don'ts:
- Don't try to access middle elements directly
- Don't forget to check for empty queue before operations
- Don't use queue when you need random access
- Don't ignore the FIFO principle
- Don't forget to handle edge cases (empty queue, single element)
- Don't use queue for LIFO operations (use stack instead)

### 🧠 Memory Aids:
- **"First In, First Out (FIFO)"**
- **"Line of people"**
- **"Enqueue to add, Dequeue to remove"**
- **"Front for removal, Rear for addition"**
- **"Check empty before dequeue"**

---

## 🔍 Debugging Tips

1. **Check queue state** - Always verify if queue is empty before operations
2. **Print queue contents** - Use helper methods to visualize
3. **Use debugger** - Step through enqueue/dequeue operations
4. **Test with edge cases** - Empty queue, single element, full queue
5. **Validate input** - Check for null or invalid inputs
6. **Monitor queue size** - Track queue growth and capacity

---

## 📚 Further Reading

- [GeeksforGeeks - Queue Data Structure](https://www.geeksforgeeks.org/queue-data-structure/)
- [LeetCode - Queue Problems](https://leetcode.com/tag/queue/)
- [HackerRank - Queue Problems](https://www.hackerrank.com/domains/data-structures?filters%5Bsubdomains%5D%5B%5D=queues)
- [Codeforces - Queue Problems](https://codeforces.com/problemset?tags=queues)

---

**🎉 Congratulations!** You've mastered Queues. Practice with the problems above to solidify your understanding!

---

**[← Back to DSA Concepts](../README.md)** | **[Previous Topic →](03 - Stacks.md)** | **[Next Topic →](05 - Strings.md)**