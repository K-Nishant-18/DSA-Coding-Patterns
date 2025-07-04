# Tree Depth-First Search (DFS) Pattern in Java

## Overview
The Tree DFS pattern explores tree paths deeply using recursion or a stack.

## Use Cases
- Find the diameter of a binary tree.
- Path sum problems.

## Approach
1. Use recursion to explore left and right subtrees.
2. Track results (e.g., maximum depth or path sum).

## Example Problem: Maximum Depth of Binary Tree
Find the maximum depth of a binary tree.

### Java Implementation
```java
class TreeNode {
    int val;
    TreeNode left, right;
    TreeNode(int val) { this.val = val; }
}

public class MaxDepth {
    public static int maxDepth(TreeNode root) {
        if (root == null) return 0;
        return 1 + Math.max(maxDepth(root.left), maxDepth(root.right));
    }
}
```

### Explanation
- **Time Complexity**: O(n).
- **Space Complexity**: O(h), where h is tree height.

## Navigation
[Back to README](README.md)