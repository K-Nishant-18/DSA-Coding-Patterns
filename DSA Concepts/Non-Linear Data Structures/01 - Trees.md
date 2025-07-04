# 🌳 Trees - Hierarchical Data Structure

## 📖 What is a Tree?

Imagine a family tree where you have grandparents at the top, parents in the middle, and children at the bottom. Each person can have multiple children, but only one parent (except the root). That's exactly what a **Tree** is in programming!

A tree is a hierarchical data structure consisting of nodes connected by edges. Each node contains data and references to its children.

```
┌─────────────────────────────────────────────────────────┐
│  Tree Visualization                                    │
│                                                       │
│                    Root (10)                          │
│                   /          \                        │
│              Left (5)      Right (15)                 │
│              /     \        /     \                   │
│         Left(3)  Right(7) Left(12) Right(18)         │
│                                                       │
│  Properties:                                          │
│  • Each node has at most 2 children (Binary Tree)    │
│  • Left child < Parent < Right child (BST)           │
│  • No cycles allowed                                  │
└─────────────────────────────────────────────────────────┘
```

## 🎯 Types of Trees

### 1. Binary Tree
Each node has at most 2 children.

### 2. Binary Search Tree (BST)
Left child < Parent < Right child.

### 3. AVL Tree
Self-balancing BST with height difference ≤ 1.

### 4. Red-Black Tree
Self-balancing BST with color properties.

### 5. B-Tree
Multi-way search tree for disk storage.

## 🧠 Tree Terminology

```
┌─────────────────────────────────────────────────────────┐
│  Tree Terminology                                     │
│                                                       │
│                    Root (10)                          │
│                   /          \                        │
│              Node (5)      Node (15)                  │
│              /     \        /     \                   │
│         Leaf(3)  Leaf(7) Leaf(12) Leaf(18)           │
│                                                       │
│  • Root: Top node (no parent)                         │
│  • Node: Element with data and children               │
│  • Leaf: Node with no children                        │
│  • Edge: Connection between nodes                     │
│  • Height: Length of longest path from root to leaf   │
│  • Depth: Distance from root to a specific node       │
└─────────────────────────────────────────────────────────┘
```

## 💡 Example 1: Binary Tree Implementation

### Problem Statement
Create a binary tree and demonstrate basic operations.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  Binary Tree Creation                                 │
│                                                       │
│  Step 1: Create root                                  │
│                   10                                  │
│                                                       │
│  Step 2: Add left child                               │
│                   10                                  │
│                   /                                   │
│                  5                                    │
│                                                       │
│  Step 3: Add right child                              │
│                   10                                  │
│                   /  \                                │
│                  5    15                              │
│                                                       │
│  Step 4: Complete tree                                │
│                   10                                  │
│                   /  \                                │
│                  5    15                              │
│                 /  \  /  \                            │
│                3    7 12  18                          │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    
    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

public class BinaryTreeDemo {
    public static void main(String[] args) {
        // Create tree:       10
        //                   /  \
        //                  5    15
        //                 /  \  /  \
        //                3    7 12  18
        
        TreeNode root = new TreeNode(10);
        root.left = new TreeNode(5);
        root.right = new TreeNode(15);
        root.left.left = new TreeNode(3);
        root.left.right = new TreeNode(7);
        root.right.left = new TreeNode(12);
        root.right.right = new TreeNode(18);
        
        System.out.println("Binary Tree created!");
        System.out.println("Root value: " + root.val);
        System.out.println("Left child of root: " + root.left.val);
        System.out.println("Right child of root: " + root.right.val);
        
        // Tree traversal
        System.out.println("\nInorder traversal:");
        inorderTraversal(root);
        System.out.println();
        
        System.out.println("Preorder traversal:");
        preorderTraversal(root);
        System.out.println();
        
        System.out.println("Postorder traversal:");
        postorderTraversal(root);
        System.out.println();
        
        // Tree properties
        System.out.println("\nTree height: " + getHeight(root));
        System.out.println("Number of nodes: " + countNodes(root));
        System.out.println("Number of leaves: " + countLeaves(root));
    }
    
    // Inorder: Left -> Root -> Right
    public static void inorderTraversal(TreeNode root) {
        if (root != null) {
            inorderTraversal(root.left);
            System.out.print(root.val + " ");
            inorderTraversal(root.right);
        }
    }
    
    // Preorder: Root -> Left -> Right
    public static void preorderTraversal(TreeNode root) {
        if (root != null) {
            System.out.print(root.val + " ");
            preorderTraversal(root.left);
            preorderTraversal(root.right);
        }
    }
    
    // Postorder: Left -> Right -> Root
    public static void postorderTraversal(TreeNode root) {
        if (root != null) {
            postorderTraversal(root.left);
            postorderTraversal(root.right);
            System.out.print(root.val + " ");
        }
    }
    
    // Calculate tree height
    public static int getHeight(TreeNode root) {
        if (root == null) {
            return -1;
        }
        return 1 + Math.max(getHeight(root.left), getHeight(root.right));
    }
    
    // Count total nodes
    public static int countNodes(TreeNode root) {
        if (root == null) {
            return 0;
        }
        return 1 + countNodes(root.left) + countNodes(root.right);
    }
    
    // Count leaf nodes
    public static int countLeaves(TreeNode root) {
        if (root == null) {
            return 0;
        }
        if (root.left == null && root.right == null) {
            return 1;
        }
        return countLeaves(root.left) + countLeaves(root.right);
    }
}
```

## 💡 Example 2: Binary Search Tree (BST)

### Problem Statement
Implement a BST with insertion, search, and deletion operations.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  BST Operations                                       │
│                                                       │
│  Insert 10:                   10                      │
│                                                       │
│  Insert 5:                    10                      │
│                              /                        │
│                             5                         │
│                                                       │
│  Insert 15:                   10                      │
│                              /  \                     │
│                             5    15                   │
│                                                       │
│  Insert 3:                    10                      │
│                              /  \                     │
│                             5    15                   │
│                            /                         │
│                           3                          │
│                                                       │
│  Search 7: Not found (would go right from 5)         │
│  Search 15: Found!                                    │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
public class BinarySearchTree {
    private TreeNode root;
    
    public BinarySearchTree() {
        this.root = null;
    }
    
    // Insert a value into BST
    public void insert(int val) {
        root = insertRec(root, val);
    }
    
    private TreeNode insertRec(TreeNode root, int val) {
        if (root == null) {
            return new TreeNode(val);
        }
        
        if (val < root.val) {
            root.left = insertRec(root.left, val);
        } else if (val > root.val) {
            root.right = insertRec(root.right, val);
        }
        
        return root;
    }
    
    // Search for a value in BST
    public boolean search(int val) {
        return searchRec(root, val);
    }
    
    private boolean searchRec(TreeNode root, int val) {
        if (root == null || root.val == val) {
            return root != null;
        }
        
        if (val < root.val) {
            return searchRec(root.left, val);
        } else {
            return searchRec(root.right, val);
        }
    }
    
    // Find minimum value in BST
    public int findMin() {
        if (root == null) {
            throw new IllegalStateException("Tree is empty");
        }
        return findMinRec(root);
    }
    
    private int findMinRec(TreeNode root) {
        if (root.left == null) {
            return root.val;
        }
        return findMinRec(root.left);
    }
    
    // Find maximum value in BST
    public int findMax() {
        if (root == null) {
            throw new IllegalStateException("Tree is empty");
        }
        return findMaxRec(root);
    }
    
    private int findMaxRec(TreeNode root) {
        if (root.right == null) {
            return root.val;
        }
        return findMaxRec(root.right);
    }
    
    // Delete a value from BST
    public void delete(int val) {
        root = deleteRec(root, val);
    }
    
    private TreeNode deleteRec(TreeNode root, int val) {
        if (root == null) {
            return null;
        }
        
        if (val < root.val) {
            root.left = deleteRec(root.left, val);
        } else if (val > root.val) {
            root.right = deleteRec(root.right, val);
        } else {
            // Node to delete found
            
            // Case 1: No child or Case 2: One child
            if (root.left == null) {
                return root.right;
            } else if (root.right == null) {
                return root.left;
            }
            
            // Case 3: Two children
            root.val = findMinRec(root.right);
            root.right = deleteRec(root.right, root.val);
        }
        
        return root;
    }
    
    // Inorder traversal (gives sorted order in BST)
    public void inorder() {
        inorderRec(root);
        System.out.println();
    }
    
    private void inorderRec(TreeNode root) {
        if (root != null) {
            inorderRec(root.left);
            System.out.print(root.val + " ");
            inorderRec(root.right);
        }
    }
    
    public static void main(String[] args) {
        BinarySearchTree bst = new BinarySearchTree();
        
        // Insert values
        bst.insert(10);
        bst.insert(5);
        bst.insert(15);
        bst.insert(3);
        bst.insert(7);
        bst.insert(12);
        bst.insert(18);
        
        System.out.println("BST created!");
        System.out.print("Inorder traversal (sorted): ");
        bst.inorder();
        
        // Search operations
        System.out.println("Search 7: " + bst.search(7));
        System.out.println("Search 20: " + bst.search(20));
        
        // Find min and max
        System.out.println("Minimum value: " + bst.findMin());
        System.out.println("Maximum value: " + bst.findMax());
        
        // Delete operation
        bst.delete(5);
        System.out.print("After deleting 5: ");
        bst.inorder();
    }
}
```

## 💡 Example 3: Level Order Traversal (BFS)

### Problem Statement
Implement level-order traversal using a queue.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  Level Order Traversal                                │
│                                                       │
│                   10                                  │
│                   /  \                                │
│                  5    15                              │
│                 /  \  /  \                            │
│                3    7 12  18                          │
│                                                       │
│  Level 0: [10]                                        │
│  Level 1: [5, 15]                                     │
│  Level 2: [3, 7, 12, 18]                             │
│                                                       │
│  Output: 10 5 15 3 7 12 18                           │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
import java.util.*;

public class LevelOrderTraversal {
    public static void levelOrder(TreeNode root) {
        if (root == null) {
            return;
        }
        
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);
        
        while (!queue.isEmpty()) {
            TreeNode current = queue.poll();
            System.out.print(current.val + " ");
            
            if (current.left != null) {
                queue.offer(current.left);
            }
            if (current.right != null) {
                queue.offer(current.right);
            }
        }
        System.out.println();
    }
    
    // Level order with level information
    public static void levelOrderWithLevels(TreeNode root) {
        if (root == null) {
            return;
        }
        
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);
        
        while (!queue.isEmpty()) {
            int levelSize = queue.size();
            System.out.print("Level: ");
            
            for (int i = 0; i < levelSize; i++) {
                TreeNode current = queue.poll();
                System.out.print(current.val + " ");
                
                if (current.left != null) {
                    queue.offer(current.left);
                }
                if (current.right != null) {
                    queue.offer(current.right);
                }
            }
            System.out.println();
        }
    }
    
    public static void main(String[] args) {
        // Create tree
        TreeNode root = new TreeNode(10);
        root.left = new TreeNode(5);
        root.right = new TreeNode(15);
        root.left.left = new TreeNode(3);
        root.left.right = new TreeNode(7);
        root.right.left = new TreeNode(12);
        root.right.right = new TreeNode(18);
        
        System.out.println("Level Order Traversal:");
        levelOrder(root);
        
        System.out.println("\nLevel Order with Level Information:");
        levelOrderWithLevels(root);
    }
}
```

## 🎯 Common Tree Patterns

### Pattern 1: Recursive Traversal
```java
public void traverse(TreeNode root) {
    if (root == null) {
        return;
    }
    
    // Process current node (preorder)
    traverse(root.left);
    // Process current node (inorder)
    traverse(root.right);
    // Process current node (postorder)
}
```

### Pattern 2: Iterative Traversal
```java
public void iterativeInorder(TreeNode root) {
    Stack<TreeNode> stack = new Stack<>();
    TreeNode current = root;
    
    while (current != null || !stack.isEmpty()) {
        while (current != null) {
            stack.push(current);
            current = current.left;
        }
        
        current = stack.pop();
        System.out.print(current.val + " ");
        current = current.right;
    }
}
```

### Pattern 3: Tree Height Calculation
```java
public int getHeight(TreeNode root) {
    if (root == null) {
        return -1;
    }
    
    int leftHeight = getHeight(root.left);
    int rightHeight = getHeight(root.right);
    
    return Math.max(leftHeight, rightHeight) + 1;
}
```

## 🚀 Practice Problems

### 🟢 Easy Level (5 Problems)
1. **[Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)** - Tree height
2. **[Symmetric Tree](https://leetcode.com/problems/symmetric-tree/)** - Mirror image check
3. **[Path Sum](https://leetcode.com/problems/path-sum/)** - Root to leaf sum
4. **[Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/)** - Recursive/iterative
5. **[Convert Sorted Array to Binary Search Tree](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)** - Balanced BST

### 🟡 Medium Level (3 Problems)
1. **[Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)** - BFS with levels
2. **[Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)** - Tree construction
3. **[Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)** - BST validation

### 🔴 Hard Level (2 Problems)
1. **[Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/)** - Path optimization
2. **[Serialize and Deserialize Binary Tree](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)** - Tree serialization

## 🎨 Key Takeaways

### ✅ Do's:
- Always check for null nodes before accessing
- Use appropriate traversal method for your problem
- Consider space complexity (recursive vs iterative)
- Handle edge cases (empty tree, single node)

### ❌ Don'ts:
- Don't forget to handle null pointers
- Don't use recursive approach for very deep trees
- Don't ignore the BST property when applicable
- Don't forget to update parent pointers when modifying tree

### 🧠 Memory Aids:
- **"Left < Root < Right"** (BST property)
- **"Preorder: Root first, Inorder: Root middle, Postorder: Root last"**
- **"BFS uses queue, DFS uses stack"**

## 🔍 Debugging Tips

1. **Print tree structure** - Use helper methods to visualize
2. **Check null pointers** - Always verify before accessing children
3. **Use debugger** - Step through recursive calls
4. **Test with small trees** - Start with simple cases

## 📚 Further Reading

- [GeeksforGeeks - Binary Tree](https://www.geeksforgeeks.org/binary-tree-data-structure/)
- [LeetCode - Tree Problems](https://leetcode.com/tag/tree/)

---

**🎉 Congratulations!** You've mastered Trees. Practice with the problems above to solidify your understanding!

---

**[← Back to DSA Concepts](../README.md)** | **[Next Topic →](02 - Heaps.md)** 