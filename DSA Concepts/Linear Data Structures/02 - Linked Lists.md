# 🔗 Linked Lists - Dynamic Data Structure

## 📖 What is a Linked List?

Imagine a treasure hunt where each clue points to the location of the next clue. You start with the first clue, follow it to the second, then to the third, and so on until you reach the treasure. That's exactly what a **Linked List** is in programming!

A linked list is a linear data structure where elements are stored in nodes, and each node contains data and a reference (pointer) to the next node in the sequence.

```
┌─────────────────────────────────────────────────────────┐
│  Linked List Visualization                             │
│                                                       │
│  Head → [10|next] → [20|next] → [30|next] → [40|null] │
│         ↑              ↑              ↑              │
│       Node 1         Node 2         Node 3         Node 4 │
│                                                       │
│  Each node contains:                                   │
│  • Data (value)                                        │
│  • Next pointer (reference to next node)              │
│  • Last node points to null (end of list)             │
└─────────────────────────────────────────────────────────┘
```

## 🎯 Types of Linked Lists

### 1. Singly Linked List
Each node has data and a pointer to the next node.

### 2. Doubly Linked List
Each node has data and pointers to both next and previous nodes.

### 3. Circular Linked List
Last node points back to the first node (forms a circle).

### 4. Circular Doubly Linked List
Combines features of doubly and circular linked lists.

## 🧠 Linked List Operations

### 1. Access (Read)
**Time Complexity**: O(n) - Linear time (must traverse from head)

```java
public int get(int index) {
    if (index < 0 || head == null) {
        return -1;
    }
    
    Node current = head;
    for (int i = 0; i < index && current != null; i++) {
        current = current.next;
    }
    
    return current != null ? current.data : -1;
}
```

### 2. Search
**Time Complexity**: O(n) - Linear time

```java
public boolean search(int value) {
    Node current = head;
    while (current != null) {
        if (current.data == value) {
            return true;
        }
        current = current.next;
    }
    return false;
}
```

### 3. Insertion
**Time Complexity**: O(1) at beginning, O(n) at end

```java
public void insertAtBeginning(int value) {
    Node newNode = new Node(value);
    newNode.next = head;
    head = newNode;
}
```

### 4. Deletion
**Time Complexity**: O(1) at beginning, O(n) at end

```java
public void deleteAtBeginning() {
    if (head != null) {
        head = head.next;
    }
}
```

## 💡 Example 1: Singly Linked List Implementation

### Problem Statement
Create a singly linked list and demonstrate basic operations.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  Singly Linked List Operations                         │
│                                                       │
│  Step 1: Create empty list                            │
│  Head → null                                          │
│                                                       │
│  Step 2: Insert 10 at beginning                       │
│  Head → [10|null]                                     │
│                                                       │
│  Step 3: Insert 20 at beginning                       │
│  Head → [20|next] → [10|null]                         │
│                                                       │
│  Step 4: Insert 30 at end                             │
│  Head → [20|next] → [10|next] → [30|null]             │
│                                                       │
│  Step 5: Delete from beginning                        │
│  Head → [10|next] → [30|null]                         │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
class Node {
    int data;
    Node next;
    
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class SinglyLinkedList {
    private Node head;
    private int size;
    
    public SinglyLinkedList() {
        this.head = null;
        this.size = 0;
    }
    
    // Insert at beginning
    public void insertAtBeginning(int data) {
        Node newNode = new Node(data);
        newNode.next = head;
        head = newNode;
        size++;
    }
    
    // Insert at end
    public void insertAtEnd(int data) {
        Node newNode = new Node(data);
        
        if (head == null) {
            head = newNode;
        } else {
            Node current = head;
            while (current.next != null) {
                current = current.next;
            }
            current.next = newNode;
        }
        size++;
    }
    
    // Insert at specific position
    public void insertAtPosition(int data, int position) {
        if (position < 0 || position > size) {
            System.out.println("Invalid position");
            return;
        }
        
        if (position == 0) {
            insertAtBeginning(data);
            return;
        }
        
        Node newNode = new Node(data);
        Node current = head;
        
        for (int i = 0; i < position - 1; i++) {
            current = current.next;
        }
        
        newNode.next = current.next;
        current.next = newNode;
        size++;
    }
    
    // Delete from beginning
    public void deleteFromBeginning() {
        if (head != null) {
            head = head.next;
            size--;
        }
    }
    
    // Delete from end
    public void deleteFromEnd() {
        if (head == null || head.next == null) {
            head = null;
            size = 0;
            return;
        }
        
        Node current = head;
        while (current.next.next != null) {
            current = current.next;
        }
        
        current.next = null;
        size--;
    }
    
    // Delete at specific position
    public void deleteAtPosition(int position) {
        if (position < 0 || position >= size) {
            System.out.println("Invalid position");
            return;
        }
        
        if (position == 0) {
            deleteFromBeginning();
            return;
        }
        
        Node current = head;
        for (int i = 0; i < position - 1; i++) {
            current = current.next;
        }
        
        current.next = current.next.next;
        size--;
    }
    
    // Search for a value
    public boolean search(int data) {
        Node current = head;
        while (current != null) {
            if (current.data == data) {
                return true;
            }
            current = current.next;
        }
        return false;
    }
    
    // Get element at position
    public int get(int position) {
        if (position < 0 || position >= size) {
            return -1;
        }
        
        Node current = head;
        for (int i = 0; i < position; i++) {
            current = current.next;
        }
        
        return current.data;
    }
    
    // Get size
    public int getSize() {
        return size;
    }
    
    // Check if empty
    public boolean isEmpty() {
        return head == null;
    }
    
    // Print list
    public void printList() {
        Node current = head;
        System.out.print("List: ");
        while (current != null) {
            System.out.print(current.data + " -> ");
            current = current.next;
        }
        System.out.println("null");
    }
    
    public static void main(String[] args) {
        SinglyLinkedList list = new SinglyLinkedList();
        
        // Insert operations
        list.insertAtBeginning(10);
        list.insertAtBeginning(20);
        list.insertAtEnd(30);
        list.insertAtPosition(15, 1);
        
        System.out.println("After insertions:");
        list.printList();
        System.out.println("Size: " + list.getSize());
        
        // Search operations
        System.out.println("Search 15: " + list.search(15));
        System.out.println("Search 25: " + list.search(25));
        
        // Get element
        System.out.println("Element at position 2: " + list.get(2));
        
        // Delete operations
        list.deleteFromBeginning();
        System.out.println("After deleting from beginning:");
        list.printList();
        
        list.deleteFromEnd();
        System.out.println("After deleting from end:");
        list.printList();
        
        list.deleteAtPosition(1);
        System.out.println("After deleting at position 1:");
        list.printList();
    }
}
```

## 💡 Example 2: Doubly Linked List

### Problem Statement
Implement a doubly linked list with forward and backward traversal.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  Doubly Linked List                                   │
│                                                       │
│  null ← [10|prev|next] ↔ [20|prev|next] ↔ [30|prev|next] → null │
│         ↑              ↑              ↑              │
│       Node 1         Node 2         Node 3         │
│                                                       │
│  Each node contains:                                   │
│  • Data (value)                                        │
│  • Previous pointer (reference to previous node)      │
│  • Next pointer (reference to next node)              │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
class DoublyNode {
    int data;
    DoublyNode prev;
    DoublyNode next;
    
    DoublyNode(int data) {
        this.data = data;
        this.prev = null;
        this.next = null;
    }
}

public class DoublyLinkedList {
    private DoublyNode head;
    private DoublyNode tail;
    private int size;
    
    public DoublyLinkedList() {
        this.head = null;
        this.tail = null;
        this.size = 0;
    }
    
    // Insert at beginning
    public void insertAtBeginning(int data) {
        DoublyNode newNode = new DoublyNode(data);
        
        if (head == null) {
            head = tail = newNode;
        } else {
            newNode.next = head;
            head.prev = newNode;
            head = newNode;
        }
        size++;
    }
    
    // Insert at end
    public void insertAtEnd(int data) {
        DoublyNode newNode = new DoublyNode(data);
        
        if (tail == null) {
            head = tail = newNode;
        } else {
            newNode.prev = tail;
            tail.next = newNode;
            tail = newNode;
        }
        size++;
    }
    
    // Delete from beginning
    public void deleteFromBeginning() {
        if (head == null) {
            return;
        }
        
        if (head == tail) {
            head = tail = null;
        } else {
            head = head.next;
            head.prev = null;
        }
        size--;
    }
    
    // Delete from end
    public void deleteFromEnd() {
        if (tail == null) {
            return;
        }
        
        if (head == tail) {
            head = tail = null;
        } else {
            tail = tail.prev;
            tail.next = null;
        }
        size--;
    }
    
    // Forward traversal
    public void printForward() {
        DoublyNode current = head;
        System.out.print("Forward: ");
        while (current != null) {
            System.out.print(current.data + " -> ");
            current = current.next;
        }
        System.out.println("null");
    }
    
    // Backward traversal
    public void printBackward() {
        DoublyNode current = tail;
        System.out.print("Backward: ");
        while (current != null) {
            System.out.print(current.data + " -> ");
            current = current.prev;
        }
        System.out.println("null");
    }
    
    public static void main(String[] args) {
        DoublyLinkedList list = new DoublyLinkedList();
        
        // Insert operations
        list.insertAtEnd(10);
        list.insertAtEnd(20);
        list.insertAtEnd(30);
        list.insertAtBeginning(5);
        
        System.out.println("Doubly Linked List:");
        list.printForward();
        list.printBackward();
        
        // Delete operations
        list.deleteFromBeginning();
        list.deleteFromEnd();
        
        System.out.println("After deletions:");
        list.printForward();
        list.printBackward();
    }
}
```

## 💡 Example 3: Circular Linked List

### Problem Statement
Implement a circular linked list where the last node points back to the first.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  Circular Linked List                                 │
│                                                       │
│                    [10] → [20] → [30]                 │
│                     ↑              ↓                  │
│                     ←───────────────                  │
│                                                       │
│  Last node points back to first node                  │
│  No null pointers (except for empty list)             │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
public class CircularLinkedList {
    private Node head;
    private int size;
    
    public CircularLinkedList() {
        this.head = null;
        this.size = 0;
    }
    
    // Insert at beginning
    public void insertAtBeginning(int data) {
        Node newNode = new Node(data);
        
        if (head == null) {
            newNode.next = newNode; // Point to itself
            head = newNode;
        } else {
            // Find last node
            Node last = head;
            while (last.next != head) {
                last = last.next;
            }
            
            newNode.next = head;
            last.next = newNode;
            head = newNode;
        }
        size++;
    }
    
    // Insert at end
    public void insertAtEnd(int data) {
        Node newNode = new Node(data);
        
        if (head == null) {
            newNode.next = newNode;
            head = newNode;
        } else {
            Node last = head;
            while (last.next != head) {
                last = last.next;
            }
            
            newNode.next = head;
            last.next = newNode;
        }
        size++;
    }
    
    // Delete from beginning
    public void deleteFromBeginning() {
        if (head == null) {
            return;
        }
        
        if (head.next == head) {
            head = null;
        } else {
            Node last = head;
            while (last.next != head) {
                last = last.next;
            }
            
            head = head.next;
            last.next = head;
        }
        size--;
    }
    
    // Print circular list
    public void printList() {
        if (head == null) {
            System.out.println("List is empty");
            return;
        }
        
        Node current = head;
        System.out.print("Circular List: ");
        do {
            System.out.print(current.data + " -> ");
            current = current.next;
        } while (current != head);
        System.out.println("(back to " + head.data + ")");
    }
    
    // Check if list is circular
    public boolean isCircular() {
        if (head == null) {
            return true;
        }
        
        Node slow = head;
        Node fast = head;
        
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            
            if (slow == fast) {
                return true;
            }
        }
        
        return false;
    }
    
    public static void main(String[] args) {
        CircularLinkedList list = new CircularLinkedList();
        
        // Insert operations
        list.insertAtEnd(10);
        list.insertAtEnd(20);
        list.insertAtEnd(30);
        
        System.out.println("Circular Linked List:");
        list.printList();
        
        System.out.println("Is circular: " + list.isCircular());
        
        // Delete operation
        list.deleteFromBeginning();
        System.out.println("After deleting from beginning:");
        list.printList();
    }
}
```

## 🎯 Common Linked List Patterns

### Pattern 1: Two Pointers (Fast and Slow)
```java
public boolean hasCycle(Node head) {
    if (head == null || head.next == null) {
        return false;
    }
    
    Node slow = head;
    Node fast = head;
    
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

### Pattern 2: Reverse Linked List
```java
public Node reverse(Node head) {
    Node prev = null;
    Node current = head;
    Node next = null;
    
    while (current != null) {
        next = current.next;
        current.next = prev;
        prev = current;
        current = next;
    }
    
    return prev;
}
```

### Pattern 3: Find Middle Node
```java
public Node findMiddle(Node head) {
    if (head == null || head.next == null) {
        return head;
    }
    
    Node slow = head;
    Node fast = head;
    
    while (fast.next != null && fast.next.next != null) {
        slow = slow.next;
        fast = fast.next.next;
    }
    
    return slow;
}
```

## 🚀 Practice Problems

### 🟢 Easy Level (5 Problems)
1. **[Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)** - Iterative and recursive
2. **[Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)** - In-place removal
3. **[Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)** - Merge operation
4. **[Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)** - Cycle detection
5. **[Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)** - Two pointers

### 🟡 Medium Level (3 Problems)
1. **[Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)** - Digit-by-digit addition
2. **[Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)** - Two pointers
3. **[Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/)** - Pair-wise swapping

### 🔴 Hard Level (2 Problems)
1. **[Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/)** - Group reversal
2. **[Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)** - Multiple list merge

## 🎨 Key Takeaways

### ✅ Do's:
- Always check for null pointers before accessing next
- Use dummy nodes for easier head manipulation
- Consider using two pointers for efficiency
- Handle edge cases (empty list, single node)

### ❌ Don'ts:
- Don't forget to update pointers when modifying list
- Don't lose references to nodes during operations
- Don't ignore memory management (in languages without GC)
- Don't use linked lists when random access is needed

### 🧠 Memory Aids:
- **"Each node points to the next"**
- **"Fast and slow pointers for cycles"**
- **"Dummy node for easier head operations"**

## 🔍 Debugging Tips

1. **Print list structure** - Use helper methods to visualize
2. **Check null pointers** - Always verify before accessing next
3. **Use debugger** - Step through pointer operations
4. **Test with small lists** - Start with 1-3 nodes

## 📚 Further Reading

- [GeeksforGeeks - Linked List](https://www.geeksforgeeks.org/data-structures/linked-list/)
- [LeetCode - Linked List Problems](https://leetcode.com/tag/linked-list/)

---

**🎉 Congratulations!** You've mastered Linked Lists. Practice with the problems above to solidify your understanding!

---

**[← Back to DSA Concepts](../README.md)** | **[Previous Topic →](01 - Arrays.md)** | **[Next Topic →](03 - Stacks.md)** 