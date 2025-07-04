# 🚶 Queues - FIFO Data Structure

## 📖 What is a Queue?

Imagine a line of people waiting to buy tickets at a movie theater. The first person who joined the line gets served first, and new people join at the end of the line. You can't cut in the middle or serve someone from the back. That's exactly what a **Queue** is in programming!

A queue is a linear data structure that follows the **FIFO (First In, First Out)** principle. Elements are added at one end (rear) and removed from the other end (front).

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

## 🎯 Types of Queues

### 1. Simple Queue
Basic FIFO queue with enqueue and dequeue operations.

### 2. Circular Queue
Queue with fixed size that reuses space when elements are dequeued.

### 3. Priority Queue
Elements are dequeued based on priority (not FIFO order).

### 4. Double-Ended Queue (Deque)
Elements can be added/removed from both ends.

## 🧠 Queue Operations

### 1. Enqueue
Add an element to the rear of the queue.
**Time Complexity**: O(1) - Constant time

### 2. Dequeue
Remove and return the element from the front of the queue.
**Time Complexity**: O(1) - Constant time

### 3. Peek/Front
View the front element without removing it.
**Time Complexity**: O(1) - Constant time

### 4. IsEmpty
Check if the queue is empty.
**Time Complexity**: O(1) - Constant time

### 5. Size
Get the number of elements in the queue.
**Time Complexity**: O(1) - Constant time

## 💡 Example 1: Simple Queue Implementation

### Problem Statement
Create a simple queue and demonstrate basic operations.

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
│  Step 5: Dequeue (remove front)                       │
│  Dequeue: 10, FRONT → [20] → [30] ← REAR              │
│                                                       │
│  Step 6: Peek (view front)                            │
│  Peek: 20 (queue unchanged)                           │
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

## 🎯 Common Queue Patterns

### Pattern 1: Queue for BFS
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

## 🚀 Practice Problems

### 🟢 Easy Level (5 Problems)
1. **[Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/)** - Stack implementation
2. **[Number of Recent Calls](https://leetcode.com/problems/number-of-recent-calls/)** - Sliding window with queue
3. **[Moving Average from Data Stream](https://leetcode.com/problems/moving-average-from-data-stream/)** - Queue for sliding window
4. **[Design Circular Queue](https://leetcode.com/problems/design-circular-queue/)** - Circular queue implementation
5. **[Design Circular Deque](https://leetcode.com/problems/design-circular-deque/)** - Double-ended queue

### 🟡 Medium Level (3 Problems)
1. **[Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)** - Monotonic queue
2. **[Open the Lock](https://leetcode.com/problems/open-the-lock/)** - BFS with queue
3. **[Perfect Squares](https://leetcode.com/problems/perfect-squares/)** - BFS approach

### 🔴 Hard Level (2 Problems)
1. **[Word Ladder](https://leetcode.com/problems/word-ladder/)** - BFS with queue
2. **[Shortest Path in Binary Matrix](https://leetcode.com/problems/shortest-path-in-binary-matrix/)** - BFS optimization

## 🎨 Key Takeaways

### ✅ Do's:
- Always check if queue is empty before dequeuing
- Use queue for FIFO operations (BFS, task scheduling)
- Consider circular queue for fixed-size scenarios
- Use priority queue when order matters

### ❌ Don'ts:
- Don't try to access middle elements directly
- Don't forget to handle queue overflow/underflow
- Don't use queue when you need random access
- Don't ignore the FIFO principle

### 🧠 Memory Aids:
- **"First In, First Out (FIFO)"**
- **"Line of people"**
- **"Enqueue to add, Dequeue to remove"**

## 🔍 Debugging Tips

1. **Print queue contents** - Use helper methods to visualize
2. **Check for empty queue** - Always verify before dequeuing
3. **Use debugger** - Step through enqueue/dequeue operations
4. **Test with edge cases** - Empty queue, single element, full queue

## 📚 Further Reading

- [GeeksforGeeks - Queue Data Structure](https://www.geeksforgeeks.org/queue-data-structure/)
- [LeetCode - Queue Problems](https://leetcode.com/tag/queue/)

---

**🎉 Congratulations!** You've mastered Queues. Practice with the problems above to solidify your understanding!

---

**[← Back to DSA Concepts](../README.md)** | **[Previous Topic →](03 - Stacks.md)** | **[Next Topic →](05 - Strings.md)** 